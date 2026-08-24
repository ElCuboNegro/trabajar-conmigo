# Trabajar conmigo

Soy Juan José Albán, Tech Lead en Grupo DeAcero. Escribí esta guía para que trabajar conmigo sea fácil desde el primer día, sin que tengas que adivinar cómo pienso ni por qué insisto en ciertas cosas.

## Cómo trabajo

Me gusta decidir con evidencia y dejar rastro escrito de las decisiones. Antes de meterle a algo grande hago un pre-mortem: me tomo un rato para pensar qué puede salir mal y cómo nos vamos a dar cuenta si pasa. Cuando diseño una prueba o un experimento, busco que pueda fallar; si solo puede salir bien, no me está diciendo nada.

Las decisiones técnicas importantes quedan documentadas con su contexto: por qué se tomaron, qué alternativas descartamos y qué tendría que cambiar para revisarlas. No es burocracia, es que en seis meses nadie se acuerda de nada, incluido yo.

Y si un proceso manual es predecible y repetitivo, lo automatizo. Prefiero pagar el costo una vez y no cada semana.

## Qué puedes esperar de mí

Feedback directo y a tiempo. Si algo no me convence te lo digo, y espero lo mismo de vuelta; nada de eso es personal. Los errores se documentan y se corrigen, no se castigan; lo que sí me incomoda es tropezar dos veces con la misma piedra sin haber escrito nada la primera vez. Y si algo se va a retrasar o está en riesgo, te vas a enterar por mí antes que por el resultado.

## Qué espero de ti

Que digas lo que piensas, sobre todo cuando crees que estoy equivocado; callarse un desacuerdo sale más caro que discutirlo. Que los cambios que afectan a más de una persona se propongan por escrito, aunque sea en corto. Y comunicación asíncrona por defecto: dame contexto suficiente para responderte sin tener que agendar una reunión.

## Disponibilidad

Respondo mensajes asíncronos en máximo 24 horas hábiles. Observo el calendario judío, así que durante Shabat y festividades no estoy disponible; lo dejo marcado en mi calendario con anticipación. Para incidentes críticos en producción aplica el esquema de on-call que acordemos, con tiempos de respuesta definidos.

## Principios técnicos

Los estándares que aplico y pido en los proyectos que lidero: infraestructura como código y todo versionado; análisis estático en pre-commit, sin excepciones; observabilidad pensada desde el diseño y no como parche posterior; máquinas de estado explícitas en los sistemas de agentes, porque un flujo implícito no se puede auditar; y SOLID y KISS como criterio real de revisión, no como póster en la pared. Las decisiones siguen un camino fijo: propuesta escrita, discusión, decisión, registro. De eso van las siguientes dos secciones.

## Cómo decidimos

Toda decisión relevante se escribe antes de construirse. Usamos tres tipos de documento según lo que se esté decidiendo: un PRD captura una necesidad de negocio, un RFC propone cambios amplios (de varios sistemas, de proceso o de metodología) y un ADR registra una decisión de arquitectura concreta. Cada uno vive donde se discute, no en una carpeta que nadie abre, y tiene autor y estado visibles.

¿Cuándo escribir uno? Mi regla es simple: si te estás preguntando si amerita propuesta, la amerita. En concreto: construir algo desde cero, meter una dependencia o herramienta nueva al stack, un contrato entre sistemas, algo que toca a más de un equipo, o que "habría que reescribir esto" te haya cruzado la mente, porque un rewrite siempre es riesgo alto. Lo que es local, reversible o medible objetivamente va directo a un PR y ya. En caso de duda, cinco minutos de conversación resuelven si vale la pena escribirlo.

Un RFC no es pedir permiso. La pregunta que hace es otra: ¿qué se nos está escapando? Cambiar una decisión en un documento cuesta poco; cambiarla en producción cuesta caro. El proceso que uso viene del [Thousand Brains Project](https://docs.thousandbrains.org/docs/request-for-comments-rfc) y de la [guía de Juan Pablo Buriticá](https://medium.com/juans-and-zeroes/a-thorough-team-guide-to-rfcs-8aa14f8e757c), ajustado con lo que hemos aprendido operándolo en el equipo:

1. **Proponer.** Revisa lo ya decidido para no reabrir discusiones cerradas, valida la idea en corto con alguien, y escribe sobre la plantilla común: qué propones y por qué, impacto, alternativas que consideraste y qué estás sacrificando. No lo pulas de más; un borrador temprano que recibe comentarios vale más que un documento perfecto que llega tarde. Si es tu primer RFC, te empareja con alguien senior que te respalde.
2. **Comentar.** Aquí está el valor del proceso. Los comentarios son perspectivas, no argumentos que ganar: cada quien trae los riesgos que ve desde lo suyo, incluida gente de producto, negocio u operación cuando el cambio los toca. La ventana de comentarios tiene fecha: entre dos días hábiles y una semana, extensible si hay una razón. Participar es opcional, pero la ventana es real; quien no comentó a tiempo ya no puede reclamar después que no lo consultaron, porque la ventana estuvo abierta y con registro. El silencio no es veto ni aprobación. Si un comentario viene marcado `[newbie]`, su autor está avisando que le falta contexto o confianza en ese terreno, y se le responde para enseñar, nunca para exhibir; eso aplica igual al senior opinando fuera de su dominio. Y si la discusión se calienta por escrito, mejor una reunión corta y la conclusión vuelve al documento.
3. **Decidir.** Decide quien es dueño del dominio afectado, no un comité. Se espera que escuche todo el feedback, no que consiga unanimidad; el diseño por comité diluye la responsabilidad hasta que nadie la tiene. Cerrada la ventana, el autor resuelve (promover, rechazar o extender) y la razón queda escrita. Quien escribe la propuesta no está obligado a implementarla; cualquiera del equipo puede tomarla. Y una cosa que hago a propósito: asignar la autoría de un RFC a alguien que normalmente habla poco. Ser autor te vuelve responsable visible de una idea sin necesidad de ser el que más grita.
4. **Archivar.** Un RFC cerrado es historia, no documentación viva; no se actualiza cuando el sistema evoluciona, para eso están los ADRs y la documentación de producción. Sirve para onboarding y para no repetir discusiones. Uno rechazado también se archiva con su porqué: le ahorra la misma conversación al siguiente.

Sobre herramientas no me caso con ninguna. Cualquier medio con comentarios por hilo que quede archivado y buscable funciona; la herramienta nunca es excusa para no escribir.

## Cómo le damos seguimiento al trabajo

Parto de una separación que me ha ahorrado muchos dolores: la decisión, el trabajo y la vista son tres cosas distintas y viven en lugares distintos. Las decisiones en sus documentos de discusión, el trabajo en issues, y la planeación en tableros que se derivan de los otros dos. Nunca duplicamos uno para simular el otro.

De esa separación salen las reglas con las que opero:

- **Todo se puede rastrear de punta a punta.** Una decisión con obra genera un epic, el epic se parte en issues, los issues se amarran a sus PRs y estos a la versión que los entrega. Esa cadena la verifican herramientas, no la memoria de nadie. Cuando se rompe (trabajo sin decisión, o una decisión ya implementada que nadie promovió), el sistema lo marca.
- **La prosa no es una relación.** Un "depende de #M" escrito en un comentario se pierde a la primera edición; la primitiva nativa del tracker (sub-issue, blocked-by, milestone, review request) sobrevive. Si la herramienta tiene la primitiva, se usa la primitiva. El texto libre acompaña, no sustituye.
- **Un issue se cierra cuando el cambio llega a producción**, no cuando se ve bien en el ambiente de pruebas. Si el tablero se ve estancado porque hay mucho terminado y poco liberado, el tablero está haciendo su trabajo: nos está enseñando un problema real de cadencia. Mover el punto de cierre para que se vea bonito es arreglar el termómetro en lugar de la fiebre.
- **Revisar un PR es trabajo, no un favor.** Una revisión solicitada tiene dueño visible, aparece en el tablero y tiene un tiempo comprometido de primera respuesta, medido en días hábiles para que los fines de semana no generen alertas falsas. El "porfa revisen" en el chat no cuenta como asignación.
- **Una regla que no bloquea nada es una sugerencia.** Cada criterio de "terminado" debe ser un check que impide el merge, o no cuenta. Los umbrales de alerta los arrancamos conservadores y los apretamos con datos, porque una alerta que la gente aprendió a ignorar cuesta más que haber empezado flojo.
- **Agentes de IA sí, pero con humano en el gate.** Los agentes proponen: parten epics en tareas, pre-revisan código. Nada se materializa sin aprobación humana explícita, un agente jamás aprueba el trabajo de otro agente, y todo merge tiene un humano con nombre que responde por él. Con agentes generando código, el cuello de botella ya no es escribir sino integrar, y el review humano se vuelve más importante, no menos: se gradúa por riesgo en lugar de aplicarse parejo.
- **El sistema señala, la gente decide.** La automatización de integridad marca inconsistencias y sugiere el arreglo, pero nunca cambia el estado de una decisión o un issue por su cuenta. Un estado que cambió solo parece correcto, y eso es peor que el desorden que intentaba corregir.

## Stack actual

En DeAcero trabajo principalmente con Google Agent Development Kit y la API de Anthropic.

---

Si algo de lo que dice este documento no se cumple en la práctica, dímelo. El feedback bidireccional también aplica a este README.
