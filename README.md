# matir Extension Packs
[Todos mis paquetes se encuentran aquí](https://marketplace.visualstudio.com/publishers/matir)
---
### **Pasos para crear un paquete**:
1. Instalar Yeoman:
   ```js
    npm install -g yo generator-code
   ```

2. Instalar Visual Studio Code Extensions
    ```js
    npm install -g vsce
   ```

3. Si no tenemos una organización, [crear una.](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/create-organization?view=azure-devops)

4. Sacar un  [PAT (Personal Access Token)](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token) en Azure Marketplace. Si no hacemos esto no podemos publicar.

    *TIP: A la hora de sacar el PAT, asegurarse de que esté disponible para todas las organizaciones.*


5. Crear un pack
   ```js
    yo code
   ```

6. Modificar el `packaje.json`. Un ejemplo sería:
    ```json
    {
        "name": "netcoreessentials",
        "displayName": "NetCoreEssentials",
        "publisher": "matir",
        "description": "yet another net-core extension pack",
        "version": "0.0.2",
        "engines": {
            "vscode": "^1.0.0"
        },
        "categories": [
            "Extension Packs"
        ],
        "extensionPack": [
            "awwsky.csharpfixformatfixed",
            "jchannon.csharpextensions",
            "jmrog.vscode-nuget-package-manager",
            "ms-dotnettools.csharp"
        ]
    }    
    ```

7. Loguearse en `vsce`. Se loguea con el nombre del publisher; en mi caso *matir*:
    ```js
    vsce login matir
    ```

8. Publicar el pack:
   ```js
   vsce publish
   ```
---
### **Actualizar pack**
Si no queremos publicarlo, lo podemos empaquetar con:
```
vsce package
```
Esto sirve especialmente para actualizar una extensión. Recordar que para actualizar, hay que cambiar la versión en el `packaje.json` y después subirlo al [Marketplace Publisher Managment](https://marketplace.visualstudio.com/manage)