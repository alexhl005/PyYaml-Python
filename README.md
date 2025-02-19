# 🛠️ YAML Configuration Updater 🛠️

## 📖 Overview
This project provides a Python script (`PRUEBA.py`) to interactively update a YAML configuration file (`vars.yml`). It's designed to help manage configuration values for different sections (wp, nc, certs) in a user-friendly way.

## 🚀 Installation
1. Ensure Python 3.x is installed
2. Clone this repository
3. Install required dependencies:
   ```bash
   pip install pyyaml
   ```

## 🎯 Usage
Run the script:
```bash
python PRUEBA.py
```

### Example Workflow
1. The script will prompt for which section to modify:
   ```
   Qué variables vas a modificar (wp, nc, certs):
   ```
2. For each variable, it will show the current value and allow you to:
   - Enter a new value
   - Press Enter to keep the current value

## ⚙️ Configuration (vars.yml)
The configuration file contains several sections:

### 🌐 Backend Configuration
```yaml
backend:
  httpPort: '8080'
```

### 🔐 Certificates Section
```yaml
certs:
  commonName:
    - '{{ wp.domain }}'
    - '{{ nc.domain }}'
    - '{{ wp.domain }}/CN={{ nc.domain }}'
  country: ES
  locality: Cordoba
  organization: ASIR
  state: Cordoba
  unitOrganization: AR
```

### 🛠️ Common PHP Modules
```yaml
common:
  phpModules:
    - php-curl
    - php-gd
    - php-mbstring
    - php-xml
    - php-xmlrpc
    - php-soap
    - php-intl
    - php-zip
    - php-imagick
```

### 🗄️ MySQL Configuration
```yaml
mysql:
  rootPassword: root
```

### ☁️ Nextcloud (nc) Configuration
```yaml
nc:
  db:
    name: ncdb
    password: ncdbu
    user: ncdbu
  domain: nc
  ip: 127.0.0.1
  virtualHostFile: '{{ nc.domain }}.conf'
```

### 🌐 WordPress (wp) Configuration
```yaml
wp:
  db:
    name: wpdb
    password: wpdbu
    user: wpdbu
  domain: wp
  ip: '"1.1.1.1"'
  virtualHostFile: '{{ wp.domain }}.conf'
```

## 🧠 Script Functions (PRUEBA.py)

### `solicitar_nuevo_valor(nombre, valor_actual)`
📝 Prompts user for new value, maintaining current if empty

### `actualizar_variables(seccion)`
🔄 Updates variables in specified section, handling nested dictionaries

### `main()`
🏃‍♂️ Main function that:
1. Loads YAML file
2. Prompts for section to modify
3. Updates variables
4. Saves changes

## ⚠️ Error Handling
- Handles missing YAML file by creating a new one
- Validates section input (wp, nc, certs)
- Preserves special keys (virtualHostFile, commonName)

## 🤝 Contributing
1. Fork the repository
2. Create a new branch
3. Make your changes
4. Submit a pull request

## 📜 License
MIT License - See [LICENSE](LICENSE) for details
