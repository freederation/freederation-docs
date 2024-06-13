# Lotería de Promoción

FREEDERATION introduce un innovador mecanismo para resolver disputas y promover nuevos proyectos Open Source dentro del ecosistema de franquicias Regen-Star. Este mecanismo se basa en una **Lotería de Promoción**, un sistema de votación y sorteo aleatorio que tiene como objetivo incentivar la participación activa de los miembros de la comunidad y apoyar el desarrollo de proyectos de alto impacto.

## La Lotería de Promoción: El Corazón del Mecanismo

En el núcleo del sistema de FREEDERATION se encuentra la **Lotería de Promoción**, un sorteo aleatorio diseñado para impulsar la participación y promoción de proyectos. Este proceso se desarrolla de la siguiente manera:

1. **Propuestas Selladas**: Los operadores de las **Meta-Islas** envían sus propuestas selladas **Sealed-Proposal** a un Banco de Veredictos. Estas propuestas contienen veredictos sobre casos abiertos en el Tribunal de Arbitraje, así como recomendaciones para la promoción de proyectos Regen-Star en incubación y la absolución de aquellos que hayan sido sancionados (GUILTY).
Una propuesta sellada **Sealed-Proposal** corresponde al Hash Keccak-256 de un bloque de atributos, 5 enteros consecutivos de 32 byes, que contiene la siguiente información:

| **Proposal Entry**      |                           |
|-----------------------|--------------------------|
| **ARBITRATION_TRIAL** | ID del Caso de denuncia sobre el cuál se determina un veredicto. Si no se especifica alguno, se asigna "0".                                                                 |
| **VEREDICT**          | Un valor entero de 32 bytes que indica el veredicto sobre el caso de denuncia (ARBITRATION_TRIAL). Se usa un múltiplo de 7 para indicar una respuesta afirmativa y declarar el veredicto como Culpable; en caso contrario, se interpreta como negativa y se declara la Inocencia. |
| **STAR_PROMOTION**    | ID de la Regen-Star en estado de incubación pero que busca promoción. Si no se especifica alguno, se asigna "0".                                                            |
| **STAR_REDEMPTION**   | ID de la Regen-Star GUILTY que puede ser perdonada. Si no se especifica alguno, se asigna "0".                                                                              |
> Esta propuesta sellada corresponde al hash Keccak-256 firmado criptográficamente con la tupla de claves Pública/Privada bajo el esquema Edwards ECDA 256619 del grupo Risetto. Se obtiene un bloque de 64 bytes que corresponde a la tupla (R,s) del punto evaluado en la curva Edwards.

2. **Generación de Número Aleatorio**: Cada VestingPeriod, la DAO de FREEDERATION genera un número aleatorio on-chain que es no predecible pero verificable. Este número se utiliza para seleccionar una propuesta sellada al azar del Banco de Veredictos. 

> En la plataforma de Internet Computer Protocol, la obtención de números aleatorios se realiza utilizando los servicios de **On-Chain Randomness** a través del **ICP management canister**.

3. **Selección del Ganador**: El autor de la propuesta sellada elegida al azar es declarado ganador de la Lotería de Promoción. Sin embargo, para reclamar su premio, debe revelar los parámetros originales de la propuesta sellada criptográficamente. 
> Es decir, debe publicarse la tupla de 5 enteros correspondientes al **Proposal Entry**. La tupla será evaluada por el contrato inteligente comparando el **committment** de la firma criptográfica previamente registrada, referenciando la misma llave pública del autor de la propuesta.

### Anulación de Jugadas
Si no coinciden la revelación y la firma criptográfica, se anula la jugada y se cancela la entrega del premio:
- Una inconsistencia en firma criptográfica implica también una sanción en reputación a la Meta-Isla responsable, reduciendo su cuenta de de **SponsorShots** y el bloqueo al sistema de votación.
- Si la jugada es inválida por otras razones (acusación no vigente, propuestas inválidas), se anula la jugada sin sanción alguna.

En ambos casos, el premio de la **Lotería de Promoción**  se acumula para el siguiente **VestingPeriod**.

## Participación y Beneficios

Para participar en la Lotería de Promoción, los operadores de Meta-Islas deben adquirir un ticket pagando una tarifa. Este sistema está restringido a un ticket por Meta-Isla por cada VestingPeriod, asegurando una distribución justa de oportunidades. Las tarifas recaudadas contribuyen al **Fondo de Gobernanza de FREEDERATION**, que se utiliza para financiar las operaciones de la plataforma y los premios de la lotería.

### Contribuciones y Distribución del Fondo de Gobernanza

El Fondo de Gobernanza se alimenta de dos fuentes principales:
1. **Tarifas de Participación**: Los tickets comprados por los operadores de Meta-Islas.
2. **Indemnizaciones**: Pagadas por las Regen-Star en los Tribunales de Arbitraje.

Un porcentaje del Fondo de Gobernanza se destina al premio de la Lotería de Promoción, incentivando así la participación activa de los operadores de Meta-Islas y fomentando la resolución de disputas y la promoción de proyectos.

## Validez de los Veredictos
Para que un veredicto emitido en una propuesta sellada sea aplicable, debe cumplir con ciertos criterios:

1. **Regen-Star Existentes**: La acusación debe dirigirse a Regen-Stars acreditadas (ACCREDITED, REDEEMED) y que no se encuentren en estado de incubación (NEBULOUS, PROMOTING) o previamente sancionadas como GUILTY.
2. **Entidad Perjudicada**: Si los miembros de una Regen-Star ya han eliminado la Meta-Isla perjudicada, se invalida el voto relacionado, ya que no existe entidad a la cual acusar.
3. **Aboluciones y Promociones**: La solicitud de absolución debe referirse a una Regen-Star en estado GUILTY que haya pagado la Tarifa de Abolución. De igual manera, el proyecto en proceso de acreditación debe mantener su estatus PROMOTING.