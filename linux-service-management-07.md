
# SERVICE MANAGEMENT

A service is a program that runs continuously in the background.

Ex: `sshd` → daemon daemon

`https://facebook.com` → HTTPS service is running

`nginx` → web/http server

Linux → Physical existing server

nginx → A logical server/service running inside the Linux server.

---

## 1. Start Service

```bash
systemctl start <service-name>
````

---

## 2. Stop Service

```bash
systemctl stop <service-name>
```

---

## 3. Check Status

```bash
systemctl status <service-name>
```

---

## 4. Restart Service

```bash
systemctl restart <service-name>
```

---

## 5. Enable Service

```bash
systemctl enable <service-name>
```

Service will start automatically whenever you start/restart the Linux server.

---

## 6. Disable Service

```bash
systemctl disable <service-name>
```

Disable the auto startup.

```
