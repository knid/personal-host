# Personal-Host

This repo contains services for my personal host.

### DNSCrypt

DNSCrypt for encrypting dns queries.

### Pi-Hole

Pi-hole for blocking domains. Ads, analytics and custom domains.

### Wireguard

Wireguard to access all other services internally, encrypt my internet traffic and connect all my other devices even if they are not connected to the same network.

## Start

Just run:

```bash
docker compose up
```

For adding wireguard peer you can access container and add manualy. But you can add via env variable too. Just open compose file and add your peer public key to **'DEFAULT_PEERS'** variable.

Example for 2 peers:

```bash
- DEFAULT_PEERS=publickey1;publickey2
```

The peer local address will be printed after running services.

Here is the wireguard example for client:

```toml
[Interface]
PrivateKey = UBRqSWnpIRlaNXzPE0vmeEukB8WQUV6tSgyag1SftVA= # Your private key
Address = 10.8.0.10/32 # This ip will be printed on console when start service
DNS = 10.0.0.11 # Internal pi-hole address

[Peer]
PublicKey = qtTMoJ41dsJzH8uWJzH+n1kW+KolKmRBR5fMSv5Zdzg= # Server Public Address
AllowedIPs = 0.0.0.0/0, ::/0 # For all connection
Endpoint = 209.124.235.80:51820 # Server ip and wg port
```

Do not forget to add pi-hole address to DNS setting in your client config for DNS Over HTTPS (DoH)

Then everything is ok.

### Check DNS leaks, DNS over HTTPS and Wireguard

- [DNS Leak Test](https://dnsleaktest.com)
- [DNS over HTTPS Test](https://1.1.1.1/help)
- [IP Check](https://ip.me)

You can check with **tcpdump** for best.

## TODO

- [ ] Create one config file for managing all services and make it more dynamic
- [ ] Peer config generator for wg
- [ ] QR Code Generator for wg peer configs
- [ ] Remove all exposed ports except wg port
- [ ] Maybe UI?
