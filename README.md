# longhorn-dashboard-ui-ansible
longhorn-dashboard-ui-ansible

## Instalación

Para instalar este proyecto, ejecute el siguiente comando utilizando Ansible:

```bash
sudo -E ansible-playbook install_longhorn_dashboard-ui.yml
```




## Desinstalación

```bash
sudo -E ansible-playbook uninstall_longhorn_dashboard-ui.yml
```


curl -v -k --http1.1 -u admin:SuperSecure456 https://longhorn.socialdevs.site/dashboard/

curl -k -u admin:SuperSecure456 https://longhorn.socialdevs.site/dashboard/







Este comando aplicará las configuraciones necesarias para desplegar el dashboard de Longhorn en su entorno.



#### Ejemplo de configuración de IngressRoute

```yaml
tls: {}  # sin secretName
# Traefik usará el defaultCertificate del TLSStore global.
```

### Creación del Archivo .env

El archivo `.env` es utilizado para definir las variables de entorno que se usarán en los playbooks de Ansible. Sigue estos pasos para crearlo:

#### Paso 1: Crear el archivo .env

Abre tu terminal.

Navega al directorio donde deseas crear el archivo `.env`.

Crea el archivo `.env` con el siguiente contenido:

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

#### Paso 2: Cargar las Variables de Entorno

Una vez creado el archivo `.env`, debes cargar las variables de entorno para que estén disponibles en tu sesión de terminal y sean accesibles para los playbooks de Ansible.

Usa el siguiente comando para cargar las variables de entorno desde el archivo `.env`:

```bash
export $(cat .env | xargs)
```

Para verificar que las variables se cargaron correctamente, puedes usar:

```bash
echo $LONGHORN_AUTH_USER
echo $LONGHORN_AUTH_PASS
```

Si las variables muestran los valores correctos, significa que se cargaron correctamente.

### Ejecutar el Playbook de Ansible

Ahora que las variables de entorno están cargadas, puedes ejecutar los playbooks de Ansible utilizando esas variables.

#### Ejemplo de ejecución del playbook

```bash
ansible-playbook -i inventory/hosts.ini playbooks/02_ingress-longhorn-internal.yml
```


export LONGHORN_AUTH_USER=admin
export LONGHORN_AUTH_PASS='SuperPassword123'

TLS global 
TLSStore 



source .env && export LONGHORN_AUTH_USER LONGHORN_AUTH_PASS && sudo -E ansible-playbook install_longhorn_dashboard-ui.yml





