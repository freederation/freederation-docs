# Aspectos a Mejorar: Votación y Privacidad

En el futuro, se debería considerar la realización de certámenes derivados de los casos seleccionados de la Lotería de Promoción para obtener la votación participativa de más jurados (Meta-Islas) y determinar veredictos sobre la absolución de una Regen-Star o la adjudicación de cargos en una denuncia.

En esta fase preliminar, el sistema propuesto no puede hacer frente a los abusos de las denuncias y puede fomentar ataques contra los proyectos Regen-Star, donde los malos actores bombardean con acusaciones falsas con tal de extraer recompensas de la Lotería de Promoción.

Para futuros desarrollos, se debe plantear una solución que reduzca el riesgo de corrupción y colusión entre los votantes. Esta solución debería capturar las deliberaciones sobre los casos de negligencia de las organizaciones Regen-Star, dedicadas a mantener el Open Source y a promover nuevos proyectos.

La futura solución deberá preservar la privacidad de los votantes, de manera que no se puedan correlacionar sus deliberaciones contabilizadas on-chain en el contrato inteligente. Para ello, se requerirán tecnologías de criptografía homomórfica y privacidad avanzada con [Pruebas de Conocimiento Cero (Zero-Knowledge Proofs)][privacy_preserving_voting_phe]:

- Este sistema debe garantizar el anonimato de los votantes y sus votos durante el proceso electoral. Su objetivo es mantener la privacidad del voto al permitir la agregación y recuento de votos de forma segura.
- El criptosistema **Paillier** se elige por su capacidad de realizar sumas y multiplicaciones en datos encriptados sin revelar el texto plano original, permitiendo la agregación segura de votos.
- El mecanismo principal habrá de codificar los votos en un único número entero, donde cada bit representa un voto para una elección específica. Esto facilita las operaciones aritméticas y la posterior Encriptación Homomórfica Parcial basada en el esquema de Paillier.
- El nuevo protocolo establece el rol de un **Organizador**, responsable de generar un par de claves pública/privada y de distribuir la clave pública a todos los votantes y agregadores. Solo el Organizador puede ver los resultados finales después de desencriptar los votos agregados.
- También se incluye el rol del **Agregador**, que recoge y valida los votos usando pruebas de conocimiento cero (ZKP) para verificar su validez sin revelar los contenidos exactos. Los votos agregados son luego enviados al Organizador para desencriptarlos y obtener los resultados finales.

La futura solución podría inspirarse en la [implementación de Galin Dinkov][privacy_preserving_voting_phe_repo], que consiste en un sistema de votación que preserva la privacidad utilizando Encriptación Homomórfica Parcial. Entre sus recomendaciones para futuros desarrollos, Dinkov sugiere abordar los riesgos de privacidad en la comunicación con los Agregadores, proponiendo el uso de una Red de Onion para ocultar las direcciones IP de los votantes.

Este sistema puede aplicarse no solo a votaciones, sino también a encuestas y otros tipos de recopilación de datos descentralizados. Esto será crucial para construir una infraestructura de verificación de hechos que apoye a los protocolos de aseguramiento de compromisos en la blockchain.

[privacy_preserving_voting_phe]: https://medium.com/@GalinDinkov/privacy-preserving-voting-system-using-partial-homomorphic-encryption-ee9a39b867f9
[privacy_preserving_voting_phe_repo]: https://github.com/CryptoVarna/phe-voting-js