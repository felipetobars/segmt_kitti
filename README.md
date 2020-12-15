## Comenzando 🚀

_Estas instrucciones te permitirán obtener una copia del proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas._

### Pre-requisitos 📋


  1. Obtener archivos en formato rosbag:
  
      Para obtener los archivos que se utilizaron para la pruebas en ROS se puede acudir al siguiente video explicativo: https://www.youtube.com/watch?v=MMZ4lwELxXc
      
      Sino se quiere recurrir al video se puede ir al repositorio de kitti2bag donde se explica el proceso de instalación y uso: https://github.com/tomas789/kitti2bag
      
      Por último se comparte el siguiente link para poder descargar los archivos ya convertidos: https://drive.google.com/drive/folders/1QH-4WMijEOBWzke8LgPS0yIx226-8hb3?usp=sharing
      
  2. Tener instalado ROS y crear un catkin workspace:
      (El proyecto se probó en Ubuntu 18.04 LTS y ROS melodic).
     
     -Para instalar ROS melodic se deben seguir los siguientes pasos: http://wiki.ros.org/melodic/Installation/Ubuntu
     
     -Para crear tu catkin workspace sigue los siguientes pasos: http://wiki.ros.org/catkin/Tutorials/create_a_workspace


### Instalación 🔧

  1. Agregar el repositorio a tu máquina local dentro de la carpeta src de tu catkin workspace:
```
git clone https://github.com/felipetobars/segmt_kitti.git
```
  2. Extraer las carpetas common y percpetion (estando dentro de la carpeta src):
  ```
mv segmt_kitti/common .
```
  ```
mv segmt_kitti/perception .
```
  3. Volver a la carpeta catkin_ws y hacer make:
  ```
catkin_make
```
  4. Agregar las variables que el entorno de ROS necesita:
  ```
source devel/setup.bash
```
  (Se recomienda tener la carpeta que tiene los archivos rosbag en la misma ubicación que segmt_kitti, es decir en la ruta **catkin_ws/src**)
  
## Ejecutando las pruebas ⚙️

  1. Para ejecutar la segmentación al suelo:
      
      En la primera terminal (dentro del catkin workspace y luego de realizar el ítem 2, 3 y 4 del apartado de **Instalación**) se ejecuta el siguiente comando:
        ```
      roslaunch segmenters_lib segment.launch
      ```
      Ahora en otra terminal (dentro del catkin workspace) se ejecuta con rosbag los datos de KITTI-dataset en bucle:

      El formato del comando es el siguiente: rosbag play -l src/<nombre_carpeta_con_todos_los_datos/<nombre_archivo_.bag>
      
      Ejemplo:
        ```
      rosbag play -l src/data_lidar/0011.bag
      ```
  2. Para ejecutar el clustering:
    
     En la primera terminal (dentro del catkin workspace) se ejecuta el siguiente comando:
        ```
      roslaunch segmenters_lib clustering_boxes.launch
      ```
     Ahora en otra terminal (dentro del catkin workspace) se ejecuta con rosbag los datos de KITTI-dataset en bucle:
        ```
      rosbag play -l src/data_lidar/0011.bag
      ```
 
  
## Autor ✒️

* **Luis Felipe Tobar** -  [felipetobars](https://github.com/felipetobars)

(En el reporte del proyecto se explica cuales son los archivos y parámetros que se pueden modificar)
