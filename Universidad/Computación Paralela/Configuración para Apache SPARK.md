Debemos tener en cuenta que la red nos permita tener una IP a nuestra máquina, por este motivo nos conectamos mediante datos moviles.

![[Pasted image 20260702072934.png]]

Buscamos cual es nuestra IP en la máquina virtual mediante el comando:
```
jonathandiaz@fedora:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:c2:a2:e1 brd ff:ff:ff:ff:ff:ff
    altname enx080027c2a2e1
    inet 10.18.160.116/24 brd 10.18.160.255 scope global dynamic noprefixroute enp0s3
       valid_lft 3364sec preferred_lft 3364sec
    inet6 fe80::52c1:fbd3:2ee7:883b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
jonathandiaz@fedora:~$ ping 8.8.8.8
```

## Instalamos JAVA
En Ubuntu: `sudo apt install openjdk-17-jdk -y`
En Fedora: `sudo dnf install java-17-openjdk-devel -y`
Para comprobar si ya estaba instalado: `java -version`

1. Actualizar sistema operativo
	1. Ubuntu: `sudo apt update` luego `sudo apt upgrade -y`
	2. Fedora: `sudo dnf upgrade -y`
2. Instalar Java
	1. Ubuntu: `sudo apt install openjdk-17-jdk -y` y comprobar con `java -version`
	2. Fedora: `sudo dnf install java-17-openjdk-devel -y`

## Apache SPARK
Spark es un framework de computación distribuida diseñado para procesar grandes volumnes de datos en clusters

Plataforma de proposito general
Trabaja con datos distribuidos
Usa memoria para acelerar el procesamiento
Tiene APIs en varios lenguajes (Python, Java, Scala y R).
Integra distintos módulos como Spark SQL, Streaming, Machine Learning y GraphX.

## Instalamos Python y PIP
En Ubuntu: `sudo apt install python3 -y`
En Fedora: `sudo dnf install python3 -y`
Para comprobar si ya estaba instalado: `python3 --version`

```bash
sudo apt install python3 python3-pip python3-venv -y`
python3 --version
pip3 --version
```

Descargar Apache Spark (Ubuntu):

```
# Descargar el archivo comprimido de Spark
wget https://dlcdn.apache.org/spark/spark-4.1.2/spark-4.1.2-bin-hadoop3.tgz

# Descomprimir el archivo
tar -xzf spark-4.1.2-bin-hadoop3.tgz

# Mover la carpeta extraída al directorio /opt/spark
sudo mv spark-4.1.2-bin-hadoop3 /opt/spark
```

Descargar Apache Spark (Fedora):

```
# Asegurar que wget esté instalado en el sistema
sudo dnf install wget -y

# Descargar el archivo comprimido de Spark
wget https://dlcdn.apache.org/spark/spark-4.1.2/spark-4.1.2-bin-hadoop3.tgz

# Descomprimir el archivo
tar -xzf spark-4.1.2-bin-hadoop3.tgz

# Mover la carpeta extraída al directorio /opt/spark
sudo mv spark-4.1.2-bin-hadoop3 /opt/spark
```

### Configuración de variables de entorno

En Ubuntu y Fedora son iguales:
```bash
nano ~/.bashrc

export JAVA_HOME=/usr/lib/jvm/java-25-openjdk
export SPARK_HOME=/opt/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
export PYSPARK_PYTHON=python3

source ~/.bashrc
```

### Verificar Spark y PySpark

Verificamos que se encuentre instalado:
```bash
spark-shell --version
pyspark --version
```

Instalamos el soporte de entornos virtuales en Fedora:
```
sudo dnf install python3-virtualenv -y
```

Crear y activar el entorno de trabajo


### Apache Spark

Instalar Jupyter Notebook
```
pip3 install notebook
jupyter notebook --version
```

Instalar PySpark y findspark
```
pip3 install pyspark findspark
```

