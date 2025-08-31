# Premier League 22-25 Attendance Report 
![premier-banner](https://external-preview.redd.it/official-premier-league-statement-everton-fc-deducted-10-v0-6SMmtIvcNEhZ-C7EA-4pzz6sylVUhOJWrbCjsuSSs7o.jpg?width=1080&crop=smart&auto=webp&s=0814b4a4feb91085693d70ce7ea937dbae1b7e5d)

# Documentación
[Premier League 22-25 Attendance Documentation](https://www.notion.so/An-lisis-de-Taquilla-Premier-League-2022-2025-2581bf5a419d807ab91ae28fa2ece197?source=copy_link)

# Dashboard
Para poder empezar, debido a que la ganancia real de un equipo se evidencia cuando juega en casa, lo primero fue filtrar ‘venue’ = “Home”. Con esto solo considero partidos de local para cada equipo.

## Medidas

- **Attendance90:** Taquilla superior al 90%
- **AvgAttendance**: Taquilla promedio
- **AvgRevenue**: Ganancia promedio
- **AvgTicketPrice**: Precio promedio de cada entrada
- **Capacity**: Capacidad de cada estadio
- **MaxRevenueByTeam**: Devuelve 1 si el partido generó la mayor ganancia para el equipo
- **TotalAttendance**: Taquilla total
- **TotalRevenue**: Ganancia total

## Filtros

### Season

Este es un filtro básico donde se puede seleccionar cada temporada (’season’)

### BIG SIX

Con este filtro, pretendo mostrar los gráficos y análisis específicamente para los equipos pertenecientes al Big Six: Arsenal, Chelsea, Liverpool, Manchester City, Manchester United y Tottenham. Los gráficos serán coloreados de acuerdo al código de color para cada equipos, obtenido de [EPL (English Premier League) Football (Soccer) Team Color Codes](https://encycolorpedia.com/teams/football/epl)

## Gráficos

### Top Teams by their Revenue

En este gráfico, si bien el plan inicial era mostrar el equipo, mientras lo realizaba, me pareció un poco más interesante mostrar también el estadio de cada uno. Por lo que creé una columna calculada ‘StadiumTeam’ que concatena ‘stadium’ y ‘team’ (valga la redundancia).

Teniendo esto listo, bastó con introducir el estadio-equipo (‘StadiumTeam’) y las ganancias totales  (medida **TotalRevenue**) ****en un *Donut chart,* filtrando esta medida con un TopN=5.

### **Attendance by Stadium and Season**

Al realizar este gráfico, me di cuenta de que las temporadas tienen un formato por año: 2023, 2024 y 2025. Es por ello que voy a modifiqué el tipo y valores de ‘season’ para que considere las temporadas según el formato correcto, es decir: 22/23, 23/24 y 24/25.

Teniendo esto corregido, bastaría con utilizar un *Ribbon chart* con la temporada (‘season’), la taquilla total (medida **TotalAttendance**) y el estadio de cada equipo (’stadium’); filtrando con el TopN=5.

### **Top Matches by their Revenue**

Para este gráfico, en primer lugar, creé una columna calculada ‘Match’ que concatene el equipo local vs el equipo visitante.

<img width="294" height="314" alt="image" src="https://github.com/user-attachments/assets/31e0cfea-3800-4706-81b6-df0e51ee0773" />


Luego, era necesario crear una medida específica para este gráfico. MaxRevenueByTeam permitió filtrar los partidos que necesitaba, mostrando los 5 partidos con mayor ganancia (‘Revenue’ y filtro topN=5 en ‘team’). Todo esto aplicado a un gráfico de barras horizontales, utilizando el partido (‘Match’), equipo (‘team’), ganancia (‘Revenue’) y la ganancia máxima por equipo y ganancia total (medidas **MaxRevenueByTeam** y **TotalRevenue**).

### Attendance Efficiency by Team

Para este interesante gráfico, opté por utilizar un *Vertical bullet chart* (publicado por [pbivizedit.com](http://pbivizedit.com/)). Me permite mostrar para cada equipo (‘team’) la taquilla promedio (medida **AvgAttendance**), teniendo en cuenta la capacidad máxima del estadio (’capacity’).

# Diseño
<img width="1087" height="788" alt="Captura de pantalla 2025-08-31 153920" src="https://github.com/user-attachments/assets/f1f58337-b639-4607-b372-a1de22b574d7" />

# Análisis

## KPIs

- Podemos observar que la gran mayoría de partidos tuvieron un estadio casi lleno, esto era de esperarse debido a la popularidad de los equipos participantes, la fidelidad de los hinchas y el interés tan enorme que genera la Premier.
- También podemos visualizar una ganancia considerable para cada equipo, superando los 130MDD en promedio.

## Gráficos

### Top teams by their Revenue

- Podemos ver que el Arsenal es el equipo con mayor ganancia, seguramente debido al precio de sus boletos.
- Le sigue el United, que, a pesar de su complicada situación, sigue generando una ganancia muy considerable para ser considerado en el top.
- Y, sorprendentemente, el West Ham se encuentra en el top, principalmente por la capacidad de más de 60mil asistentes en su estadio.

### Attendance by Stadium

- El imponente Old Trafford se alza como el estadio con más asistentes en las 3 temporadas analizadas, esto debido a tener la mayor capacidad de la Premier. Esto refleja una gran fidelidad de parte de su afición, a pesar de pasar por la peor etapa en su historia.
- Reforzando el hallazgo del gráfico circular, el London Stadium, del West Ham, refleja la segunda mayor cantidad de asistentes en el análisis. Ciertamente, la capacidad y efectividad de asistencia son los puntos clave.

### Top Matches by their Revenue

- No es sorpresa que el Arsenal vs Liverpool sea el partido con mayor recaudación, ya que ambos han sido serios contendientes al título en los últimos años. Especialmente el Arsenal, desde la llegada de Arteta.
- Les sigue el derbi de Manchester, cuya aparición tampoco es sorprendente. Como se mencionó, la capacidad del estadio del United y la rivalidad contra el equipo ciudadano jugaron un papel fundamental en las ganancias para este partido.

### Average Attendance Efficiency

- Nuevamente, el dominante, en términos de de asistencia y efectividad de asistencia, es el United. Esto refuerza que el United es uno de los equipos más grandes del planeta, que, a pesar de sus situación, sigue teniendo una afición fiel y que está dispuesta a llenar Old Trafford cada partido.
- Y, otra vez, West Ham, se posa como segundo lugar en términos de eficiencia de asistentes. Como se explicó, el London Stadium tiene una de las capacidad más grandes y, a la vez, una afición que los seguirá a pesar de estar luchando puestos de descenso en los últimos años.
