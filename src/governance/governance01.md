# Tribunales de Arbitraje

El Tribunal de Arbitraje actúa como un mecanismo de control y resolución de conflictos dentro de la plataforma FREEDERATION. Facilita un canal de denuncias a través del cual los miembros de la comunidad pueden presentar acusaciones detalladas sobre negligencia en proyectos Open Source en las Regen-Star o acciones inapropiadas por parte de las Meta-Islas. 

## Mecanismo de Denuncias

### Publicación de Denuncias

Los miembros de las comunidades dentro de FREEDERATION tienen la facultad de publicar denuncias detalladas sobre actos de negligencia de los administradores de los proyectos en las Regen-Star, o sobre acciones inapropiadas de moderación por parte de las Meta-Islas. 

Estas denuncias se publican como hilos de discusión en la plataforma Nostr, estableciendo así un canal formal para radicar y legitimar las acusaciones en el **Banco de Acusaciones** del **Tribunal de Arbitraje**.


### Radicación y Legitimación de Denuncias

#### Legitimación por Votación

los **Sponsors** verificados (utilizando su token **SponsorAccount**), tienen la facultad de votar a favor o en contra de las denuncias publicadas en hilos de discusión dentro de la plataforma **Nostr**.

Estas votaciones no incurren en algún costo de transacción, pero tampoco otorgan beneficios económicos a los **Sponsors**. Simplemente se considera que este tipo de usuarios (aquellos que buscan la promoción de sus contenidos), son directamente afectados por los conflictos entre las comunidades a causa de una mala gestión de contenidos, negligencia en el mantenimiento del proyecto Open Source o corrupción dentro de las organizaciones Regen-Star.

Por ende, FREEDERATION considera que las denuncias son legítimas si cuentan con un umbral mínimo de diferencia por el conteo votaciones a favor menos las votaciones en contra. Es decir, si una denuncia tiene `55` votaciones a favor y `40` en contra, el umbral de votación diferencial es de `15`.

#### Radicación de la Denuncia por parte de las Meta-Islas

Una vez publicada una denuncia en **Nostr** y sometida a votación por parte de los **Sponsors**, los operadores de las Meta-Islas  radican la denuncia en el **Banco de Acusaciones** del **Tribunal de Arbitraje**. Al hacerlo, obtienen un token numérico que representa la denuncia interpuesta. 

Una denuncia contiene los siguientes atributos:

| **Atributo**          | **Descripción**                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| **ACCUSED_ID**         | El ID de la entidad acusada (Regen-Star o Meta-Isla).                            |
| **CASE_TYPE**          | Un valor enumerado de los tipos de casos que se gestionan en Nostr.             |
| **ACCUSATION-POST**    | El ID de la publicación Nostr JSON con detalles del caso.                       |
| **RETRIBUTION**        | Retribución económica que se paga como indemnización a la parte afectada.       |
| **PRESTIGE-DAMAGE**    | Cantidad de puntos que se descuentan del Prestigio de la Regen-Star.            |
| **INDEMNIFIED_PARTY**  | Dirección de wallet donde se pagará a la parte indemnizada. Por defecto 0.      |


Durante este proceso, se especifica el tipo de falta según las categorizaciones disponibles, y las sanciones varían dependiendo del tipo de falta y la entidad responsable (Regen-Star o Meta-Isla).
A continuación se describen los tipos de denuncias correspondientes al atributo **CASE_TYPE** ,  enumerados por identificador:

| **Item**                    | **Descripción**                                                                                                  |
|-----------------------------|------------------------------------------------------------------------------------------------------------------|
| **FAKE_PROJECT**            | La acusación recae sobre la Regen-Star por representar un proyecto o causa que no existe o no representa el valor comunitario anunciado. |
| **MISREPRESENTATION**       | La acusación recae sobre la Regen-Star por suplantación de un proyecto Open Source existente y recaudar fondos sin retribuir a los autores originales. |
| **IP_PROJECT_INFRIGEMENT**  | La acusación recae sobre la Regen-Star por el uso indebido de creaciones intelectuales sin el permiso de los autores. |
| **EMBEZZLEMENT**            | La acusación recae sobre la Regen-Star por malversación de fondos del proyecto Open Source.                       |
| **NFT_PLAGIARISM**          | La acusación recae sobre la Regen-Star al publicar una colección de NFTs sin licencia de uso o plagio artístico.  |
| **DEV_NEGLIGENCE**          | La acusación recae sobre la Regen-Star por mala gestión e incumplimiento en las tareas de desarrollo.             |
| **PROJECT_SECURITY_HAZZARD**| La acusación recae sobre la Regen-Star por propagar software defectuoso que acarrea riesgos de ciberseguridad.    |
| **HARMFUL_PROJECT**         | La acusación recae sobre la Regen-Star por propagar contenido digital dañino para la comunidad.                   |
| **BAD_COMMUNITY_MANAGEMENT**| La acusación recae sobre la Regen-Star por mala gestión de comunidades o falta de moderación.                     |
| **BAD_GOVERANNCE**          | La acusación recae sobre la Regen-Star por corrupción en su gobernanza o toma de poder sin equilibrio participativo. |
| **HARMFUL_ISLAND**          | Acusación recae sobre la Meta-Isla por propagar contenido dañino o spam.                                          |
| **MISGUIDED_CURATION**      | Acusación recae sobre la Meta-Isla por asignar mal las categorizaciones de búsqueda.                              |
| **IP_ISLAND_INFRIGEMENT**   | Acusación recae sobre la Meta-Isla por el uso indebido de creaciones intelectuales sin el permiso de los autores. |
| **SPONSORSHIP_FRAUD**       | Acusación recae sobre la Meta-Isla por promover contenido fraudulento de sponsors.                                |
| **ISLAND_COMPLIANCE_FAILURE**| Acusación recae sobre la Meta-Isla por fallar a sus compromisos (Inactivo, usado en el futuro).                  |

### Denuncias Inválidas

Una denuncia puede ser descartada si no cuenta con el suficiente umbral de voto diferencial para considerarse legítima.Por eso es importante la calificación de los **Sponsors** durante el proceso.

Otras causas de anulación de la denuncias son:
- Inconsistencias con respecto al sujeto acusado (**Regen-Star** no existente o vigente). 
- Que la **Regen-Star** no esté operativa: es decir, o bien no se encuerntra **Acreditada** para operar (no cuenta con el status de  `ACCREDITED` o `REDEEMED`), o bien haya sido sancionada y permanece en estado `GUILTY ` por otro veredicto anterior.
- Que la **Meta-Isla** perjudicada haya sido removida de la franquicia a la cuál pertenecía (**Regen-Star**) por efecto de la moderación de los **Regen-Planets**.


## Sanciones y Penalizaciones

### Sanciones para las Meta-Islas

1. **Confiscación y Clausura del Token**: La sanción para una Meta-Isla incluye la confiscación y clausura de su token, así como la confiscación de sus comisiones no reclamadas durante el **VestingPeriod** presente.

2. **Penalización al Regen-Planet Asociado**: Cuando una Meta-Isla es sancionada, también se penaliza al Regen-Planet asociado. Se retira la titularidad de la participación accionaria de sus dueños y su derecho a gestionar el activo. Las comisiones se confiscan y el Regen-Planet pasa a ser administrado tutelarmente por su Regen-Star. Todas las comisiones recaudadas por el Regen-Planet sancionado se destinan al **Fondo de Cobertura de Riesgos** de la Regen-Star.

3. **Sanción Económica**: La sanción económica se paga del **Fondo de Cobertura de Riesgos** de la Regen-Star. Si no se puede pagar la sanción en su totalidad, se considera una falta de toda la organización representada por la Regen-Star, degradando su prestigio y limitando sus derechos y actividad económica. Esto implica cambiar su status a `GUILTY`.

### Sanciones para las Regen-Star

1. **Extrema Gravedad**: Las sanciones a una Regen-Star son de extrema gravedad, usualmente relacionadas con casos de corrupción en su gobernanza o mala gestión del proyecto Open Source. La penalización afecta a toda la organización de miembros asociados.

2. **Limitación de Actividad Económica**: Se limita la actividad económica de toda la organización de la Regen-Star y se neutraliza su capacidad de respaldar compromisos.

3. **Degradación de Status**: La sanción degrada el status de la Regen-Star a `GUILTY`, resultando en la pérdida de puntaje de prestigio. También implica una sanción económica que debe ser pagada del Fondo de Cobertura de Riesgos de la Regen-Star.

4. **Absolución**: Para que una Regen-Star pueda ser absuelta en el futuro, debe cancelar el total de la deuda de las sanciones económicas del Fondo de Cobertura de Riesgos y pagar una cuota extraordinaria correspondiente a la **Tarifa de Absolución**.


Cabe aclarar que una Regen-Star afectada por las faltas de sus Meta-Islas no habría de perder necesariamente su status de Acreditada a Culpable (`GUILTY`), mientras tenga capacidad de pagar las indemnizaciones del Fondo de Cobertura de Riesgos. 
Pero en caso de no lograr cumplir su sanción, pasa al status de `GUILTY` y permanecerá en ese estado hasta que logre ser absuelta en una votación de la **Lotería de Promoción**.
Por otro lado, las acusaciones contra la propia Regen-Star implican una falta institucional grave que puede quitar la legitimidad a todo el proyecto. Además de la sanción económica, pierde su acreditación y su status pasa a GUILTIY instantáneamente.

## Absoluciones
Cuando una Regen-Star es degradada al estatus `GUILTY`, se neutraliza su capacidad de producir Meta-Islas o Regen-Planets. Sus miembros asociados pierden el derecho a participar en certámenes de votación y en la Lotería de Promoción, y tampoco pueden operar actividades comerciales en nombre de la organización.

Además, se descuenta un grado de Prestigio por cada VestingPeriod que transcurra desde su sanción. Durante este estado, las Regen-Planets pueden solicitar un juicio de absolución en la Lotería de Promoción, pagando la correspondiente Tarifa de Abolución cada VestingPeriod para participar como Regen-Star elegible. Cabe destacar que es un requisito cancelar la totalidad de las indemnizaciones adeudadas para poder acceder a este beneficio.

Si la Regen-Star obtiene la absolución, reinicia su evolución con el estatus de "redimida" (REDEEMED) y pierde todo derecho a respaldar a otras Regen-Star en estado de incubación, lo que significa que su **SponsorshipBonus** se fija en `0`.