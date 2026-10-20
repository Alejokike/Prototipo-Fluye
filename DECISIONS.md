# DECISIONS

| Decisión | Variante elegida | Por qué | Tipo |
|---|---|---|---|
| Roles de usuario | Tres roles: Propietario, Administrador y Operador. Se elimina «Administrador propietario». | Alineado con DC-013 (15-oct): tres roles, puede haber varios Propietarios. | Decisión |
| Datos de ejemplo del equipo | Solo Carolina Mejías es Propietaria; Pedro Medina, Eduardo Paredes y el resto de administradores quedan como Administrador. | Un solo titular en la demo. Las reglas con varios Propietarios (transferencia, quién edita a quién) siguen abiertas en la especificación de BE-00. | Decisión (19-oct) |
| Navegación en móvil | Sin barra inferior ni botón principal flotante; se navega con el menú lateral. | La barra inferior duplicaba la navegación del menú. | Decisión (19-oct) |
| Textos de ayuda | Se eliminan subtítulos, pistas de campo y tooltips con información redundante. | Reducir ruido; solo queda la ayuda que aporta algo que la pantalla no dice. | Decisión (19-oct) |
| Tarjetas | No se anidan tarjetas dentro de tarjetas; los indicadores dentro de un panel van planos (ej. «Cobranza de hoy» en Inicio). | Jerarquía visual más limpia. | Decisión (19-oct) |
| Controles de formulario | Desplegables, carga de archivos, áreas de texto y barras de scroll con el estilo del Design System; botones del formulario a la derecha, la acción principal al final. | Consistencia con DS 1.2.0. | Decisión (19-oct) |
