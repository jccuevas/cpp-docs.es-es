---
title: "Error del compilador de recursos RW2002 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2002"
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador de recursos RW2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error de análisis  
  
### Posibles causas del error:  
  
1.  **Tipo de acelerador requerido \(ASCII o VIRTKEY\)**  
  
     El campo `type` en la instrucción **ACCELERATORS** debe contener el valor ASCII o el valor VIRTKEY.  
  
2.  **Se esperaba BEGIN en la tabla de aceleradores**  
  
     La palabra clave **BEGIN** debe seguir inmediatamente a la palabra clave **ACCELERATORS**.  
  
3.  **Se esperaba BEGIN en el cuadro de diálogo**  
  
     La palabra clave **BEGIN** debe seguir inmediatamente a la palabra clave **DIALOG**.  
  
4.  **Se esperaba BEGIN en el menú**  
  
     La palabra clave **BEGIN** debe seguir inmediatamente a la palabra clave **MENU**.  
  
5.  **Se esperaba BEGIN en RCData**  
  
     La palabra clave **BEGIN** debe seguir inmediatamente a la palabra clave **RCDATA**.  
  
6.  **Se esperaba la palabra clave BEGIN en la tabla de cadenas**  
  
     La palabra clave **BEGIN** debe seguir inmediatamente a la palabra clave **STRINGTABLE**.  
  
7.  **No se pueden volver a usar constantes de cadena**  
  
     Se está utilizando el mismo valor dos veces en una instrucción **STRINGTABLE.** Asegúrese de que no se mezclan valores decimales y hexadecimales superpuestos.  Cada uno de los identificadores en una **STRINGTABLE** debe ser único.  Para obtener la máxima eficacia, utilice constantes contiguas que comiencen con un múltiplo de 16.  
  
8.  **Carácter de control fuera del intervalo \[^A \- ^Z\]**  
  
     Uno de los caracteres de control en la instrucción **ACCELERATORS** no es válido.  El carácter que sigue al símbolo de intercalación \(**^**\) debe estar entre la A y la Z, ambas incluidas.  
  
9. **No se permiten menús vacíos**  
  
     Una palabra clave **END** aparece antes de definir cualquier elemento de menú en la instrucción **MENU**.  El compilador de recursos no permite menús vacíos.  Asegúrese de que no haya ningún signo de comillas abierto dentro de la instrucción **MENU**.  
  
10. **Se esperaba END en el cuadro de diálogo**  
  
     La palabra clave **END** debe aparecer al final de una instrucción **DIALOG**.  Asegúrese de que no queden comillas abiertas de la instrucción anterior.  
  
11. **Se esperaba END en el menú**  
  
     La palabra clave **END** debe aparecer al final de una instrucción **MENU**.  Asegúrese de que no haya ningún signo de comillas abierto o una pareja que no coincida de instrucciones **BEGIN** y **END**.  
  
12. **Se esperaba una coma en la tabla de aceleradores**  
  
     El compilador de recursos requiere una coma entre los campos `event` e *idvalue* en la instrucción **ACCELERATORS.**  
  
13. **Se esperaba un nombre de clase de control**  
  
     El campo `class` de una instrucción **CONTROL** en la instrucción **DIALOG** debe ser de uno de los siguientes tipos: BUTTON, COMBOBOX, EDIT, LISTBOX, SCROLLBAR, STATIC o uno definido por el usuario.  Asegúrese de que la clase se haya escrito correctamente.  
  
14. **Se esperaba un nombre de fuente**  
  
     El campo *typeface* de la opción FONT en la instrucción **DIALOG debe ser una cadena de caracteres ASCII entre signos de comillas tipográficas.** Este campo especifica el nombre de una fuente.  
  
15. **Se esperaba un valor de identificador para menuitem**  
  
     La instrucción **MENU debe contener un campo** *menuID* que especifique el nombre o el número que identifica los recursos del menú.  
  
16. **Se esperaba cadena de menú**  
  
     Cada instrucción **MENUITEM** y **POPUP** debe contener un campo *text*, que es una cadena incluida entre signos de comillas tipográficas que especifica el nombre del elemento de menú o menú emergente.  Una instrucción **MENUITEMSEPARATOR** no requiere una cadena entre comillas.  
  
17. **Se esperaba un valor de comando numérico**  
  
     El compilador de recursos esperaba un campo *idvalue* numérico en la instrucción **ACCELERATORS.** Asegúrese de que haya utilizado una constante `#define` para especificar el valor y de que la constante se haya escrito correctamente.  
  
18. **Se esperaban constantes numéricas en la tabla de cadenas**  
  
     Una constante numérica, definida en una instrucción `#define`, debe seguir inmediatamente a la palabra clave **BEGIN** en una instrucción **STRINGTABLE**.  
  
19. **Se esperaba un tamaño de punto numérico**  
  
     El campo *pointsize* de la opción FONT en la instrucción **DIALOG debe tener un valor entero de tamaño de punto.**  
  
20. **Se esperaba una constante de diálogo numérica**  
  
     Una instrucción **DIALOG requiere valores enteros para los campos** *x, y, width* y *height.* Asegúrese de que estos valores estén incluidos después de la palabra clave **DIALOG** y de que no sean negativos.  
  
21. **Se esperaba una cadena en STRINGTABLE**  
  
     Se espera una cadena después de cada valor *stringid* en una instrucción **STRINGTABLE.**  
  
22. **Se esperaba un comando acelerador de cadena o de constante**  
  
     El compilador de recursos no pudo determinar el tipo de clave configurada para el acelerador.  El campo `event` en la instrucción **ACCELERATORS podría no ser válido.**  
  
23. **Se esperaba un número para el identificador**  
  
     Se esperaba un número para el campo `id` de una instrucción de control en la instrucción **DIALOG.** Asegúrese de que haya un número o una instrucción `#define` para el identificador de control.  
  
24. **Se esperaba una cadena entre comillas en la clase del cuadro de diálogo**  
  
     El campo `class` de la opción CLASS en la instrucción **DIALOG debe ser un entero o una cadena entre signos de comillas tipográficas.**  
  
25. **Se esperaba una cadena entre comillas en el título del cuadro de diálogo**  
  
     El campo `captiontext` de la opción CAPTION en la instrucción **DIALOG debe ser una cadena de caracteres ASCII entre signos de comillas tipográficas.**  
  
26. **Archivo no encontrado: 'nombredearchivo'**  
  
     No se encontró el archivo especificado en la línea de comandos del compilador de recursos.  Compruebe si se ha movido el archivo a otro directorio y si se ha escrito correctamente el nombre del archivo o la ruta de acceso.  Los archivos se buscan en función de si utilizan la variable de entorno **INCLUDE** o la configuración de Visual Workbench si está disponible.  
  
27. **Los nombres de fuentes deben ser ordinales**  
  
     El campo *pointsize* en la instrucción FONT debe ser un entero, no una cadena.  
  
28. **Acelerador no válido**  
  
     No se reconoció un campo `event` en la instrucción **ACCELERATORS o tenía una longitud de más de dos caracteres.**  
  
29. **Tipo de acelerador no válido \(ASCII o VIRTKEY\)**  
  
     El campo `type` en la instrucción **ACCELERATORS** debe contener el valor ASCII o el valor VIRTKEY.  
  
30. **Carácter de control no válido**  
  
     Uno de los caracteres de control en la instrucción **ACCELERATORS** no es válido.  Un carácter de control válido se compone de una sola letra que va a continuación de un símbolo de intercalación \(^\).  
  
31. **Tipo de control no válido**  
  
     Cada instrucción de control en una instrucción **DIALOG** debe ser una de las siguientes: CHECKBOX, COMBOBOX, CONTROL, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, ICON, LISTBOX, LTEXT, PUSHBUTTON, RADIOBUTTON, RTEXT, SCROLLBAR.  Asegúrese de que estas instrucciones de control estén escritas correctamente.  
  
32. **Tipo no válido**  
  
     El tipo de recurso no se encontraba entre los tipos definidos en el archivo WINDOWS.h.  
  
33. **Se esperaba una cadena de texto u ordinal en el control**  
  
     El campo *text* de una instrucción **CONTROL** en una instrucción **DIALOG debe ser una cadena de texto o una referencia ordinal al tipo de control.** Si se usa un ordinal, asegúrese de que haya una instrucción `#define` para el control.  
  
34. **Los paréntesis no coinciden**  
  
     Asegúrese de que haya cerrado todos los paréntesis abiertos en la instrucción **DIALOG.**  
  
35. **Valor inesperado en RCDATA**  
  
     Los valores de *raw\-data* en la instrucción **RCDATA** deben ser enteros o cadenas, separados cada uno por una coma.  Asegúrese de que no haya olvidado una coma o unas comillas alrededor de una cadena.  
  
36. **Subtipo de menú desconocido**  
  
     El campo *item\-definition* de la instrucción **MENU** solo puede contener las instrucciones **MENUITEM** y **POPUP**.