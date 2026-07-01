Inicializado docker en la linea de comando
```
docker login
```

Debe mostrar el mensaje de
login succeeded

```
docker build -t web-nginx .
```

El comando es hasta -t, lo demás es un tag

Si compilo correctamente debo ejecutar

```
docker run -d -p 8080: 80 web-nginx
```

Si me devuelve un ID de varios dígitos significa que sí se está ejecutando 

---
Descripción:
Publicar la imagen en Docker Hub para la visualización del landing page que ya se encuentra en el repositorio personal de GitHub.

Estructura de la carpeta:
Al ser un computador empresarial, se optó por crear una carpeta personal donde se realizarán los trabajos correspondientes.

WEB
	1er P
			Landing Page
				Imagenes
					iconGlobo.svg
				.dockerignore
				Dockerfile
				index.html
				README.md
			Practica1

Esta estructura es la que se encuentra subida al repositorio en GitHub.

Instrucciones:

**Idea de extension: Que bajo la carpeta de Explorer en VS Code muestre la ventana de youtube lo que esuches, sea de youtube, spotify, etc**

