# 🚀 Let's Encrypt Manager Stack

A stack for automatic SSL certificate management from Let's Encrypt using [nginx-proxy/acme-companion](https://github.com/nginx-proxy/acme-companion).

## 📦 Deployment

```bash
docker-compose up --build -d
```

## 🔒 Enabling External Access to Containers with SSL from Let's Encrypt

To make a container accessible from outside, you need to:

- add the `letsencrypt-network` network
- fill in `VIRTUAL_PORT` - the container port that requires external access
- fill in `VIRTUAL_HOST` - the domain on which the container will be accessible
- fill in `LETSENCRYPT_HOST` - the domain for which the certificate is issued
- fill in `LETSENCRYPT_EMAIL` - email for certificate request

Example:

```yml
  kibana:
    environment:
      VIRTUAL_PORT: 5601
      VIRTUAL_HOST: ${VIRTUAL_HOST}
      LETSENCRYPT_HOST: ${LETSENCRYPT_HOST}
      LETSENCRYPT_EMAIL: ${LETSENCRYPT_EMAIL}
    networks:
      - letsencrypt-network

networks:
  letsencrypt-network:
    name: letsencrypt-network
    external: true
```

## ℹ️ About

This project uses [nginx-proxy/acme-companion](https://github.com/nginx-proxy/acme-companion) for automatic SSL certificate acquisition and renewal from Let's Encrypt. The acme-companion component works in conjunction with nginx-proxy to provide seamless HTTPS integration for your Docker containers.

## 📄 License

This project is dual-licensed under:

- [Apache License 2.0](LICENSE-APACHE)
- [MIT License](LICENSE-MIT)

You may choose either license for your use.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.
