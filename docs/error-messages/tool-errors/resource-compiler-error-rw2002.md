---
title: Error del compilador de recursos RW2002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2002
dev_langs:
- C++
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b90a0800708af41037325204a00c808bec2a7d20
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080863"
---
# <a name="resource-compiler-error-rw2002"></a>Error del compilador de recursos RW2002

Error de análisis

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. **Tipo de acelerador requerido (ASCII o VIRTKEY)**

   El campo `type` de la instrucción **ACCELERATORS** debe contener el valor ASCII o VIRTKEY.

1. **Se esperaba BEGIN en la tabla de aceleradores**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **ACCELERATORS** .

1. **Se esperaba BEGIN en el cuadro de diálogo**

   El **comenzar** palabra clave debe seguir inmediatamente el **diálogo** palabra clave.

1. **Se esperaba BEGIN en el menú**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **MENU** .

1. **Se esperaba BEGIN en RCData**

   La palabra clave **BEGIN** debe aparecer inmediatamente después de la palabra clave **RCDATA** .

1. **Palabra clave BEGIN esperada en la tabla de cadenas**

   El **comenzar** palabra clave debe seguir inmediatamente el **STRINGTABLE** palabra clave.

1. **No se puede volver a usar las constantes de cadena**

   Utiliza el mismo valor dos veces en un **STRINGTABLE** instrucción. Asegúrese de que no mezcla superpuestos valores hexadecimales y decimales. Cada identificador en un **STRINGTABLE** deben ser únicos. Para obtener la máxima eficacia, utilice constantes contiguas que comienzan en un múltiplo de 16.

1. **Carácter fuera del intervalo de control [^ A - ^ Z]**

   Un carácter de control en la instrucción **ACELERAtors** no es válido. El carácter que sigue al símbolo de intercalación (**^**) debe estar comprendido entre A y Z, ambos inclusive.

9. **No se permiten de menús vacíos**

   Un **final** palabra clave aparece antes de cualquier elemento de menú se define en el **menú** instrucción. El compilador de recursos no permite menús vacíos. Asegúrese de que no tiene ningún signo de comillas abierto dentro de la **menú** instrucción.

10. **Se esperaba END en el cuadro de diálogo**

   El **final** palabra clave se debe producir al final de un **diálogo** instrucción. Asegúrese de que no hay ningún queden comillas abiertas de la instrucción anterior.

11. **Se esperaba END en el menú**

   La palabra clave **END** debe aparecer al final de una instrucción **MENU** . Asegúrese de que no tenga ningún signo de comillas abierto ni una pareja que no coincida de instrucciones **BEGIN** y **END** .

12. **Se esperaba una coma en la tabla de aceleradores**

   El compilador de recursos requiere una coma entre los campos `event` idvalue *y* de la instrucción **ACCELERATORS** .

13. **nombre de la clase control esperado**

   El `class` campo de un **CONTROL** instrucción en el **diálogo** instrucción debe ser uno de los siguientes tipos: botón, COMBOBOX, EDIT, LISTBOX, barra de desplazamiento, estático, o definido por el usuario. Asegúrese de que la clase está escrita correctamente.

14. **Se esperaba el nombre de fuente**

   El campo *typeface* de la opción FONT de la instrucción **DIALOG** debe ser una cadena de carácter ASCII entre comillas dobles. Este campo especifica el nombre de una fuente.

15. **Valor de identificador esperado para menuitem**

   La instrucción **MENU** debe contener un campo *menuID* que especifique el nombre o el número que identifica el recurso de menú.

16. **Cadena de menú esperada**

   Cada una de las instrucciones **MENUITEM** y **POPUP** debe contener un campo *text* , que es una cadena entre comillas dobles que especifica el nombre del elemento de menú o menú de elemento emergente. Un **MENUITEM separador** instrucción no requiere ninguna cadena entre comillas.

17. **Se esperaba un valor numérico de comando**

   El compilador de recursos esperaba un valor numérico *idvalue* campo el **ACELERADORES** instrucción. Asegúrese de que ha usado un `#define` constante para especificar el valor y que la constante está escrita correctamente.

18. **Se esperaba una constante numérica en la tabla de cadenas**

   Una constante numérica, definida en una instrucción `#define` debe seguir inmediatamente a la palabra clave **BEGIN** en una instrucción **STRINGTABLE** .

19. **Se esperaba el tamaño de punto numérico**

   El campo *pointsize* de la opción FONT en la instrucción **DIALOG** debe ser un valor entero de tamaño de punto.

20. **se esperaba una constante numérica del cuadro de diálogo**

   Un **diálogo** instrucción requiere valores enteros para el *x, y, ancho*, y *alto* campos. Asegúrese de que estos valores se incluyen después de la **diálogo** palabra clave y que no son negativos.

21. **Se esperaba una cadena en STRINGTABLE**

   Se espera una cadena después de cada valor *stringid* en una instrucción **STRINGTABLE** .

22. **Comando de Acelerador de constante o cadena esperado**

   El compilador de recursos no pudo determinar qué tipo de clave se va a configurar para el acelerador. El campo `event` de la instrucción **ACCELERATOS** podría no ser válido.

23. **Se espera un número para el Id.**

   Se esperaba un número para el `id` campo de una instrucción de control en el **diálogo** instrucción. Asegúrese de que tiene un número o `#define` instrucción para el identificador de control.

24. **Se esperaba una cadena entre comillas en la clase de cuadro de diálogo**

   El campo `class` de la opción CLASS en la instrucción **DIALOG** debe ser un entero o una cadena entre comillas dobles.

25. **Se esperaba una cadena entre comillas en el título del cuadro de diálogo**

   El campo `captiontext` de la opción CAPTION de la instrucción **DIALOG** debe ser una cadena de caracteres ASCII entre comillas dobles.

26. **No se encontró el archivo: nombre de archivo**

   No se encontró el archivo especificado en la línea de comandos del compilador de recursos. Compruebe si el archivo se ha movido a otro directorio y si se ha escrito correctamente el nombre de archivo o ruta de acceso. Los archivos se buscan usando la **INCLUDE** variable de entorno o la configuración de Workbench Visual, si está disponible.

27. **Los nombres de fuente deben ser ordinales**

   El *pointsize* campo en la instrucción de la fuente debe ser un entero, no una cadena.

28. **Acelerador no válido**

   Un campo `event` en la instrucción **ACCELERATORS** no se reconoce o tenía más de dos caracteres de longitud.

29. **Tipo de acelerador no válido (ASCII o VIRTKEY)**

   El campo `type` de la instrucción **ACCELERATORS** debe contener el valor ASCII o VIRTKEY.

30. **carácter de control no válido**

   Un carácter de control en la instrucción **ACELERAtors** no es válido. Un carácter de control válido se compone de una letra (solo) siguiendo un símbolo de intercalación (^).

31. **Tipo de control no válido**

   Cada instrucción de control en un **diálogo** instrucción debe ser uno de los siguientes: CHECKBOX, COMBOBOX, CONTROL, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, icono, LISTBOX, LTEXT, PUSHBUTTON, RADIOBUTTON, RTEXT, barra de desplazamiento. Asegúrese de que estas instrucciones de control estén escritas correctamente.

32. **Tipo no válido**

   El tipo de recurso no estuvo entre los tipos definidos en el archivo WINDOWS.h.

33. **Cadena de texto u ordinal esperada en el control**

   El *texto* campo de un **CONTROL** instrucción en el **diálogo** instrucción debe ser una cadena de texto o una referencia ordinal al tipo de control. Si usa un ordinal, asegúrese de que tiene una instrucción `#define` para el control.

34. **Paréntesis no coincidentes**

   Asegúrese de que haya cerrado todos los paréntesis abiertos en el **diálogo** instrucción.

35. **Valor inesperado en RCData**

   Los valores de *datos sin procesar* de la instrucción **RCDATA** deben ser enteros o cadenas, separados por una coma. Compruebe que no olvidó una coma o unas comillas de una cadena.

36. **Subtipo de menú desconocido**

   El *definición de elemento* campo de la **menú** instrucción solo puede contener **MENUITEM** y **emergente** instrucciones.