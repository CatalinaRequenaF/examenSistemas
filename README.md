## 1- Introducción  
Esta es la documentación del despliegue de nuestra aplicación a través de Docker-compose. 

## 2- Configuración del archivo docker-compose.yml.  
Para configurar el archivo docker-compose tenemos que instanciar los volúmenes e imagenes necesarias para nuestra aplicación.   
Primero creamos un servicio (volumen) mysql e indicamos el nombre de la imagen en la que desplegaremos la app. 
En este caso, es `mariadb`.

![image](https://user-images.githubusercontent.com/91744454/173106838-b489468f-ee30-4f74-b3a9-9bbb68a6130c.png)  

Ahora creamos otro volumen para el nginx, en nuestro caso `alpine`:  
![image](https://user-images.githubusercontent.com/91744454/173107123-366b19a7-a242-4049-8d59-7cddbd29afae.png)  

Por último, creamos un último volumen para nuestro servidor. Al ser Java, emplearemos `tomcat`.
![image](https://user-images.githubusercontent.com/91744454/173107370-1329ac21-edcd-4bc1-8b63-177037f11960.png)

------------------------------------------------------------
## 3- Creación del Dockerfile
![image](https://user-images.githubusercontent.com/91744454/173111311-6442d137-0539-441d-a888-1a928b7dd399.png)

Deberemos de utilizar archivos xml para que tomcat pueda ejecutarlos:   
![image](https://user-images.githubusercontent.com/91744454/173110399-3ea88d90-3d15-486a-b698-6b609aa3639c.png)  
![image](https://user-images.githubusercontent.com/91744454/173110417-a5fc040f-6fac-46a9-873a-51526de61f55.png)  


## 4- Preparación y subida de la imagen a dockerhub.  
  
Ya tenemos los volumenes y archivos necesarios para poder desplegar nuestra aplicación.  
  
Una vez tengamos todo en el mismo local (aplicación y archivos docker) ejecutamos el comando `docker-compose up` para correr el contenedor  
![image](https://user-images.githubusercontent.com/91744454/173114090-7e8b0627-6e40-4a7b-940e-c94284451f42.png)

![image](https://user-images.githubusercontent.com/91744454/173114014-d95425fa-909a-4fe5-ae30-283cab65bedf.png)

Para comprobar que todo está bien, introducimos `docker-compose ps`  
![image](https://user-images.githubusercontent.com/91744454/173115539-fcdb440e-ecae-4369-8647-6e41460b1253.png)


A continuación tenemos que subir la imagen de nuestro proyecto, ejecutando `login docker build` 
![image](https://user-images.githubusercontent.com/91744454/173116467-909e7623-59d4-48b9-9293-62060702aeb4.png)


Como paso final, haremos un `docker push`

El resultado se verá así  
![image](https://user-images.githubusercontent.com/91744454/173117077-77aa87dc-4389-4e97-972e-31743019083f.png)


## 6- Annexos 
