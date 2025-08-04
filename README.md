# longhorn-dashboard-ui-ansible

Este proyecto utiliza Ansible para desplegar y gestionar el dashboard de Longhorn en tu entorno.

---

## Instalación

Para instalar este proyecto, ejecuta el siguiente comando utilizando Ansible:

```bash
sudo bash -c 'source .env && export LONGHORN_AUTH_USER LONGHORN_AUTH_PASS && sudo -E ansible-playbook install_longhorn_dashboard-ui.yml'
```

Este comando aplicará las configuraciones necesarias para desplegar el dashboard de Longhorn.

---

## Desinstalación

Para desinstalar el dashboard de Longhorn, utiliza el siguiente comando:

```bash
sudo bash -c 'source .env && export LONGHORN_AUTH_USER LONGHORN_AUTH_PASS && sudo -E ansible-playbook uninstall_longhorn_dashboard-ui.yml'
```

---

## Configuración del Archivo `.env`

El archivo `.env` es utilizado para definir las variables de entorno necesarias para los playbooks de Ansible. Sigue estos pasos para crearlo:

### Paso 1: Crear el archivo `.env`

1. Abre tu terminal.
2. Navega al directorio donde deseas crear el archivo `.env`.
3. Crea el archivo `.env` con el siguiente contenido:

```bash
sudo nano .env
```

Añade las siguientes líneas al archivo `.env`:

```bash
LONGHORN_AUTH_USER=admin
LONGHORN_AUTH_PASS=SuperSecure456
# Puedes añadir otras variables como TRAEFIK_AUTH_USER y TRAEFIK_AUTH_PASS si lo necesitas
```

Guarda y cierra el archivo presionando `Ctrl + X`, luego `Y` para confirmar y `Enter`.

### Paso 2: Cargar las Variables de Entorno

Una vez creado el archivo `.env`, carga las variables de entorno para que estén disponibles en tu sesión de terminal:

```bash
export $(cat .env | xargs)
```

Para verificar que las variables se cargaron correctamente, usa:

```bash
echo $LONGHORN_AUTH_USER
echo $LONGHORN_AUTH_PASS
```

Si las variables muestran los valores correctos, significa que se cargaron correctamente.

---

## Ejecución de Playbooks de Ansible

### Ejemplo de Ejecución

Con las variables de entorno cargadas, puedes ejecutar los playbooks de Ansible. Por ejemplo:

```bash
sudo ansible-playbook -i inventory/hosts.ini playbooks/02_ingress-longhorn-internal.yml
```

---

## Ejemplo de Configuración de `IngressRoute`

Si necesitas configurar un `IngressRoute`, aquí tienes un ejemplo:

```yaml
tls: {}  # sin secretName
# Traefik usará el defaultCertificate del TLSStore global.
```

---

## Ejemplo de Uso con `curl`

Puedes probar el acceso al dashboard de Longhorn utilizando `curl`:

```bash
curl -v -k --http1.1 -u admin:SuperSecure456 https://longhorn.socialdevs.site/dashboard/
```

---

Este archivo ha sido optimizado para eliminar redundancias, corregir errores y mejorar la claridad de las instrucciones.
