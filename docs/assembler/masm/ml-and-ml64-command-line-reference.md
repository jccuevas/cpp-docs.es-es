---
title: "ML and ML64 Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ML"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/W* MASM compiler option"
  - "/c MASM compiler option"
  - "/EP MASM compiler option"
  - "/Fe MASM compiler option"
  - "/Zp MASM compiler option"
  - "/AT MASM compiler option"
  - "/Zm MASM compiler option"
  - "/Sf MASM compiler option"
  - "/Sp MASM compiler option"
  - "/w MASM compiler option"
  - "/Fl MASM compiler option"
  - "/coff MASM compiler option"
  - "/St MASM compiler option"
  - "/Cx MASM compiler option"
  - "/Sl MASM compiler option"
  - "/Cu MASM compiler option"
  - "MASM (Microsoft Macro Assembler), ML command-line reference"
  - "/FPi MASM compiler option"
  - "/Zf MASM compiler option"
  - "ML environment variable"
  - "/Fr MASM compiler option"
  - "/help MASM compiler option"
  - "/Sa MASM compiler option"
  - "/Zd MASM compiler option"
  - "/I MASM compiler option"
  - "/? MASM compiler option"
  - "/Bl MASM compiler option"
  - "/Fm MASM compiler option"
  - "/Fo MASM compiler option"
  - "command-line reference [ML]"
  - "/Sn MASM compiler option"
  - "/Gd MASM compiler option"
  - "/D* MASM compiler option"
  - "environment variables, ML"
  - "/Gc MASM compiler option"
  - "/F* MASM compiler option"
  - "/Sc MASM compiler option"
  - "/H MASM compiler option"
  - "/Zs MASM compiler option"
  - "/omf MASM compiler option"
  - "/Sg MASM compiler option"
  - "/Cp MASM compiler option"
  - "/Zi MASM compiler option"
  - "/nologo MASM compiler option"
  - "/Sx MASM compiler option"
  - "/WX MASM compiler option"
  - "/Ss MASM compiler option"
  - "command line, reference [ML]"
  - "/Ta MASM compiler option"
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# ML and ML64 Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ensambla y enlaza uno o más archivos de código fuente del lenguaje de ensamblado.  Las opciones de la línea de comandos distinguen entre mayúsculas y minúsculas.  
  
 Para obtener más información sobre ml64.exe, vea [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## Sintaxis  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### Parámetros  
 `options`  
 las opciones enumeradas en la tabla siguiente.  
  
|Opción|Acción|  
|------------|------------|  
|**\/AT**|Compatibilidad de minúsculo\-memoria\-modelo de permisos.  Los mensajes de error de los permisos de construcciones de código que cumplen los requisitos para .com da formato a los archivos.  Observe que esto no es equivalente a la directiva de [.MODEL](../../assembler/masm/dot-model.md)**TINY** .<br /><br /> no disponible en ml64.exe.|  
|**\/Bl** `filename`|selecciona un vinculador alternativo.|  
|**\/c**|Ensambla únicamente.  No vinculado.|  
|**\/coff**|Representa el tipo de formato común del archivo \(COFF\) objeto de módulo de objeto.  Necesario generalmente para el desarrollo en lenguaje de ensamblado de Win32.<br /><br /> no disponible en ml64.exe.|  
|**\/Cp**|Conserva el caso de los identificadores de usuario.|  
|**\/Cu**|Asigna todos los identificadores a mayúsculas \(valor predeterminado\).<br /><br /> no disponible en ml64.exe.|  
|**\/Cx**|Conserva el caso en símbolos públicos como extern.|  
|**\/D** `symbol`\[\[\=`value`\]\]|Define una macro de texto con el nombre especificado.  Si falta `value` , está en blanco.  Varios tokens separados por espacios deben escribirse entre comillas.|  
|**\/EP**|Genera una lista preprocesada de origen \(enviada a STDOUT\).  Vea **\/Sf**.|  
|**\/ERRORREPORT** \[ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND** \]|Si ml.exe o ml64.exe produce errores en tiempo de ejecución, puede utilizar **\/ERRORREPORT** para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información sobre **\/ERRORREPORT**, vea [\/errorReport \(Informar de los errores del compilador\)](../../build/reference/errorreport-report-internal-compiler-errors.md).|  
|**\/F** `hexnum`|Establece el tamaño de la pila a bytes de `hexnum` \(es lo mismo que **\/link\/STACK**:`number`\).  El valor se debe expresar en notación hexadecimal.  debe haber un espacio entre **\/F** y `hexnum`.|  
|**\/Fe** `filename`|nombres el archivo ejecutable.|  
|**\/Fl**\[\[`filename`\]\]|genera una lista de código ensamblada.  Vea **\/Sf**.|  
|**\/Fm**\[\[`filename`\]\]|Crea un archivo de mapa del vinculador.|  
|**\/Fo** `filename`|nombres un archivo objeto.  Vea la sección comentarios para obtener más información.|  
|**\/FPi**|Genera el emulador corrección\-UPS para la aritmética flotante \(lenguaje mixto solo\).<br /><br /> no disponible en ml64.exe.|  
|**\/Fr**\[\[`filename`\]\]|Genera un archivo de explorador .sbr de origen.|  
|**\/FR**\[\[`filename`\]\]|Genera un formulario extendido de un archivo de explorador .sbr de origen.|  
|**\/Gc**|Especifica el uso de llamada y las convenciones de nomenclatura de FORTRAN o la función de Pascal\-estilo.  Igual que **OPTION LANGUAGE:PASCAL**.<br /><br /> no disponible en ml64.exe.|  
|**\/Gd**|Especifica el uso de la llamada y las convenciones de nomenclatura de la función de C.  Igual que **OPTION LANGUAGE:C**.<br /><br /> no disponible en ml64.exe.|  
|**\/GZ**|Especifica el uso de la llamada y las convenciones de nomenclatura de la función \_\_stdcall.  Igual que **OPTION LANGUAGE:STCALL**.<br /><br /> no disponible en ml64.exe.|  
|**\/H** `number`|Limita nombres externos a caracteres significativos del número.  El valor predeterminado es 31 caracteres.<br /><br /> no disponible en ml64.exe.|  
|**\/help**|Llamadas QuickHelp para obtener ayuda sobre el ml.|  
|**\/I** `pathname`|Establece la ruta del archivo de inclusión.  Un máximo de 10 opciones de **\/I** está permitido.|  
|**\/nologo**|Suprime los mensajes para el ensamblado correcto.|  
|**\/omf**|Representa el tipo de formato de archivo \(OMF\) object module de módulo de objeto.  **\/omf** implica **\/c**; ML.exe no admite la vinculación de objetos OMF.<br /><br /> no disponible en ml64.exe.|  
|**\/Sa**|Activa la lista de toda la información disponible.|  
|**\/safeseh**|Marca el objeto como no debe contener ningún controlador de excepciones o contener controladores de excepciones que todos se declaran con [.SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> no disponible en ml64.exe.|  
|**\/Sf**|Agrega la lista de primer paso para mostrar el archivo.|  
|**\/Sl** `width`|Establece el ancho de la lista de origen en caracteres por línea.  El intervalo es de 60 a 255 o 0.  El valor predeterminado es 0.  Igual que el ancho de [PÁGINA](../../assembler/masm/page.md) .|  
|**\/Sn**|Desactiva la tabla de símbolos al generar una lista.|  
|**\/Sp** `length`|Establece la longitud de página lista de origen en líneas por página.  El intervalo es de 10 a 255 o 0.  El valor predeterminado es 0.  Igual que la longitud de [PÁGINA](../../assembler/masm/page.md) .|  
|**\/Ss** `text`|Especifica el texto de la lista de origen.  Igual que el texto de [SUBTÍTULO](../../assembler/masm/subtitle.md) .|  
|**\/St** `text`|Especifica el título para la lista de origen.  Igual que el texto de [TÍTULO](../../assembler/masm/title.md) .|  
|**\/Sx**|Gira condicionales falsos en la lista.|  
|**\/Ta** `filename`|Ensambla el archivo de código fuente cuyo nombre no tiene la extensión .asm.|  
|**\/w**|Igual que **\/W0\/WX**.|  
|**\/W** `level`|Establece el nivel de advertencia, donde `level` \= 0, 1, 2, 3.|  
|**\/WX**|Devuelve un código de error si se generan advertencias.|  
|**\/X**|Omita la ruta de acceso del entorno INCLUDE.|  
|**\/Zd**|Genera información de número de línea en el archivo objeto.|  
|**\/Zf**|Crea todo el público de símbolos.|  
|**\/Zi**|Genera información CodeView en archivo objeto.|  
|**\/Zm**|Habilitala opción de**M510** a fin de optimizar con MASM 5,1.<br /><br /> no disponible en ml64.exe.|  
|**\/Zp**\[\[`alignment`\]\]|estructuras de los Paquetes en el límite de byte especificado.  `alignment` puede ser 1, 2 o 4.|  
|**\/Zs**|Realiza una verificación sintáctica únicamente.|  
|**\/?**|Muestra un resumen de la sintaxis de la línea de comandos de ML.|  
  
 `filename`  
 Nombre del archivo.  
  
 `linkoptions`  
 Las opciones de vínculo.  Para obtener más información, consulte [Opciones del vinculador](../../build/reference/linker-options.md).  
  
## Comentarios  
 Algunas opciones de la línea de comandos cuando ML y a ML64 son posición\-sensibles.  Por ejemplo, porque el ML y ML64 pueden aceptar varias opciones de **\/c** , cualquier opción correspondiente de **\/Fo** debe especificarse antes de **\/c**.  El ejemplo de línea de comandos siguiente muestra una especificación de archivo objeto para cada especificación del archivo de ensamblado:  
  
 **ml.exe \/Fo a1.obj \/c a.asm \/Fo b1.obj \/c b.asm**  
  
## Variables de entorno  
  
|Variable|Descripción|  
|--------------|-----------------|  
|INCLUIR|Especifica la ruta de búsqueda de archivos de inclusión.|  
|ml|Especifica opciones de la línea de comandos predeterminadas.|  
|TMP|Especifica la ruta de acceso de los archivos temporales.|  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)   
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)