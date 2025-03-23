# Ensambles: Consenso y Potenciacion

Análisis de clasificación mediante ensambles para construir un modelo para averiguar qué medicamento podría ser apropiado para un futuro paciente con la misma enfermedad.

Para este ejercicio comenzamos cargando la base de datos y procesando la información para poderla utilizar
<br>![image](https://github.com/user-attachments/assets/0a6d3e58-7b11-419c-9f8b-c5f69bbb2eea) ![image](https://github.com/user-attachments/assets/efdd68d4-1a08-4564-8e4d-9fc515c0ab95)

***Random Forest***

Separamos los grupos de entrenamiento y prueba y corremos el modelo
<br>![image](https://github.com/user-attachments/assets/a643b899-ecc9-4384-9b59-ec1e01c57895)
<br>![image](https://github.com/user-attachments/assets/495c4c18-2fc0-4441-80fb-e6a44c78a8c4)

Evaluamos la precision y score F1 de los resultados
<br>![image](https://github.com/user-attachments/assets/8d125167-3065-4249-95ad-50044de32e56)
<br>![image](https://github.com/user-attachments/assets/06856dd1-73af-42dc-9c87-950b8bc6f355)

A primera instancia parece ser bastante confiable pero también podría utilizar optimización, gráficamente podemos ver la importancia de cada una de las características evaluadas
<br>![image](https://github.com/user-attachments/assets/e73aecf2-75c1-48e6-b451-3d3576eb5b12)
<br>![image](https://github.com/user-attachments/assets/73f78687-eb5a-447d-b693-8965e08e4fec)

El método ***Rando Forest*** parece ajustarse muy bien de primera instancia con una precisión general de 95% y valores F1 bastante altos también con la característica Na_to_K siendo la más importante, seguida por la presión sanguínea.

***Gradient Boosted Trees***

Para probar este método solo necesitamos volver a separar nuestros grupos de prueba y entrenamiento y correr el modelo de la misma forma
<br>![image](https://github.com/user-attachments/assets/49ce6b31-6cb2-48b4-b58a-cf08607a8161)

De igual manera evaluamos su desempeño
<br>![image](https://github.com/user-attachments/assets/0680295b-0984-427c-8f5c-5553d081ad3f)
<br>![image](https://github.com/user-attachments/assets/b400a238-14ec-4630-b6f9-33b1b72772a4)

De igual forma observamos la ponderación de las características
<br>![image](https://github.com/user-attachments/assets/446227b7-fa2e-44a4-902e-4f0c9cb45e86)

Con el método ***Gradient Boosting*** obtenemos una precisión de 100% resaltando la característica de Na to K como la más importante, aunque generalmente tener un modelo 100% centero podría considerarse que hubo un sobre ajuste y que posiblemente la información no fuera confiable, al haber trabajado con esta base de datos anteriormente y conocer cómo se desempeñó con modelos anteriores, considera que es confiable.

***Alternativa de Gradient Boosting***

Para probar la forma alternativa cambiamos la máxima profundidad a 2 para intentar reducir la complejidad del modelo esperando una solución más óptima.
<br>![image](https://github.com/user-attachments/assets/b03f0802-acd8-4c98-9931-f6e02ff68107)
<br>![image](https://github.com/user-attachments/assets/4cb9db05-3640-43d5-8a74-24759a30161d)
<br>![image](https://github.com/user-attachments/assets/d7a1053f-ecbb-43ab-8501-779eeb2af1af)

Utilizando la forma alterna con un máximo de profundidad de 2 obtenemos los mismos scores y precisión pero podemos observar una mayor ponderación para la característica Na to K y menor para presión sanguínea y la edad; aunque creo que los resultados pueden ser confiables, me inclinaria a utilizar el resultado anterior para no apoyarse tanto en una sola característica.

***AdaBoost Classifier***

Por ultimo probamos con AdaBoost para intentar optimizar aún más el modelo
<br>![image](https://github.com/user-attachments/assets/20aff27c-c7fa-4d9e-a89c-70adec24f575)
<br>![image](https://github.com/user-attachments/assets/e48baf2e-7172-424e-b447-cfc737c7afa5)

A primera instancia obtenemos una precisión de 85 % pero viendo los valores individuales vemos que los resultados no son confiables para la mayoría de los casos.
Probamos usar el clasificador SVM para mejorar el método:
<br>![image](https://github.com/user-attachments/assets/2e5a3839-961c-4e41-8b4e-1b7d27f4d284)
<br>![image](https://github.com/user-attachments/assets/631452bf-6017-487a-9b0e-051b9f41659b)

Utilizando el método de ***AdaBoost Classifier*** con el estimador SVC nos da un resultado diferente con incluso menor precisión general, para este caso el método que se ajusta mejor para nuestros datos sería el de Gradient Boosting Trees.

<br>![image](https://github.com/user-attachments/assets/08e84fd1-afd5-4363-b0f9-7868a66ff370)

Probando el método elegido con un nuevo paciente, obtenemos que el medicamento apropiado seria el Y.
