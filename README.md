# SICaMoT: Stress Inverssion Calcuator of Moment Tensors
A Web application to calculate the stress inversion for a group of moment tensors of seismic events within predefined geographical areas, with the help of the STRESSINVERSE and Gisola softwares. The calculations are updated as new data are identified for each defined region. For the description of the calculation areas, area sources that have been proposed in the recent past for the Greek area are used, and there is also the possibility to manually design the desired surface, thus covering more possible applications for the needs of the individual researcher. Additionally, the desired group of moment tensors can be filtered by date, magnitude, depth and rake.

## Screenshots

![image](https://github.com/Kayieni/thesis_gisola_plugin/assets/44552188/7b67c96d-e88f-46a9-bedc-172c6beb3500)

![image](https://github.com/Kayieni/thesis_app/assets/44552188/7136c764-ea1b-4e33-a924-01642e4f7e6c)

![image](https://github.com/Kayieni/thesis_app/assets/44552188/038464cb-43d1-415b-888c-af9a64296858)

![image](https://github.com/Kayieni/thesis_app/assets/44552188/3989ea5d-a1dc-42ba-8802-2bba94b31b1e)  ![image](https://github.com/Kayieni/thesis_app/assets/44552188/12cb545c-23f9-4b70-bb40-0f51b2266c09)


## Installation

1. Firstly, you need to deploy the environment:
```Bash
sudo apt-get update -y
sudo apt-get install -y default-libmysqlclient-dev build-essential
sudo apt-get install -y pkg-config
cd mt_stress_inversion_calculator
conda env create -f environment.yml
cd mt_stress_inversion_calculator/Stressinverse/Programs_PYTHON && chmod +x *.py
```

2. Then, you need to have a MySQL instance up and running. Therefore, you can install MySQL server on your PC, or run a dockerized version of it. In the latter case you need to have Docker store the data, otherwise after reboot you would need to re-run it.

3. Assuming, that Dockerized version is used, then run:
```Bash
conda activate gisola
cd mt_stress_inversion_calculator
mkdir mysql-docker && cd mysql-docker
docker-compose up -d
```

4. Run the application
```Bash
conda activate gisola
cd mt_stress_inversion_calculator
flask run --debug
```

If it takes too long because it loads all old events found, you should limit it accordingly at obs.py file lines 116, 117.
If duplicated MTs, do in terminal `docker compose down; docker compose up -d`
