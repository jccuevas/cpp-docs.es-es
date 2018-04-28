---
title: Referencia de línea de comandos de ML y ML64 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ML
dev_langs:
- C++
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da3fb143aeaaf6fa8cf31c45b31707fa01bf6898
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-and-ml64-command-line-reference"></a>Referencia de la línea de comandos de ML y ML64
Ensambla y se proporcionan vínculos a uno o más archivos de código fuente de lenguaje de ensamblado. Las opciones de línea de comandos distinguen mayúsculas de minúsculas.  
  
 Para obtener más información sobre ml64.exe, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `options`  
 Las opciones enumeradas en la tabla siguiente.  
  
|Opción|Acción|  
|------------|------------|  
|**/AT**|Habilita la compatibilidad del modelo de memoria pequeña. Permite que los mensajes de error para las construcciones de código que infringen los requisitos para los archivos de formato .com. Tenga en cuenta que esto no es equivalente a la [. MODELO](../../assembler/masm/dot-model.md) **MINÚSCULO** directiva.<br /><br /> No está disponible en ml64.exe.|  
|**/BL** `filename`|Selecciona a un vinculador alternativo.|  
|**/c**|Ensambla solo. No se vincula.|  
|**/COFF**|Genera el tipo de formato format (COFF) común de archivo objeto de módulo de objeto. Suelen ser necesarios para desarrollo de lenguaje de ensamblado de Win32.<br /><br /> No está disponible en ml64.exe.|  
|**CP**|Conserva las mayúsculas y minúsculas de todos los identificadores de usuario.|  
|**/Cu**|Asigna todos los identificadores en mayúsculas (valor predeterminado).<br /><br /> No está disponible en ml64.exe.|  
|**/CX**|Conserva el caso de los símbolos públicos y extern.|  
|**/D** `symbol`[[=`value`]]|Define una macro de texto con el nombre especificado. Si `value` es falta, está en blanco. Varios tokens separados por espacios deben incluirse entre comillas.|  
|**/EP**|Genera una lista de origen preprocesada (que se envía a STDOUT). Vea **/Sf**.|  
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **PROMPT** &AMP;#124; **COLA** &AMP;#124; **ENVIAR** ]|Si ml.exe o ml64.exe produce un error en tiempo de ejecución, puede usar **/ERRORREPORT** para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información acerca de **/ERRORREPORT**, consulte [/errorReport (informar de errores de compilador interno)](../../build/reference/errorreport-report-internal-compiler-errors.md).|  
|**/F** `hexnum`|Establece el tamaño de pila `hexnum` bytes (Esto equivale a **/vínculo/pila**:`number`). El valor se debe expresar en notación hexadecimal. Debe haber un espacio entre **/F** y `hexnum`.|  
|**/FE** `filename`|Nombre para el archivo ejecutable.|  
|**/Fl**[[`filename`]]|Genera una lista de código ensamblado. Vea **/Sf**.|  
|**/FM**[[`filename`]]|Crea un archivo de asignación del vinculador.|  
|**/FO** `filename`|Nombres de un archivo de objeto. Para obtener más información, vea la sección Comentarios.|  
|**/Fpi**|Genera el emulador reparaciones aritmética de coma flotante (solo lenguaje mixto).<br /><br /> No está disponible en ml64.exe.|  
|**/Fr**[[`filename`]]|Genera un archivo .sbr de explorador de código fuente.|  
|**/FR**[[`filename`]]|Genera un formulario extendido de un archivo .sbr de explorador de origen.|  
|**/GC**|Especifica el uso de la función de estilo FORTRAN o Pascal de llamada y convenciones de nomenclatura. Igual que **opción idioma: PASCAL**.<br /><br /> No está disponible en ml64.exe.|  
|**/Gd**|Especifica el uso de la función de estilo C de llamada y convenciones de nomenclatura. Igual que **opción idioma: C**.<br /><br /> No está disponible en ml64.exe.|  
|**/GZ**|Especifica el uso de __stdcall función llamada y convenciones de nomenclatura.  Igual que **opción idioma: STCALL**.<br /><br /> No está disponible en ml64.exe.|  
|**/H** `number`|Restringe los nombres externos a número caracteres significativos. El valor predeterminado es 31 caracteres.<br /><br /> No está disponible en ml64.exe.|  
|**/help**|Las llamadas ayuda rápida para obtener ayuda acerca de aprendizaje automático.|  
|**/ I.** `pathname`|Ruta de acceso de conjuntos de archivo de inclusión. Un máximo de 10 **/I** se permiten las opciones.|  
|**/nologo**|Suprime los mensajes para el ensamblado correcto.|  
|**/OMF**|Genera el tipo de formato (OMF) de archivo de módulo de objeto de módulo de objeto.  **/OMF** implica **/c**; ML.exe no admite la vinculación de objetos OMF.<br /><br /> No está disponible en ml64.exe.|  
|**/SA**|Activa la lista de toda la información disponible.|  
|**/ SAFESEH**|Marca el objeto como que contiene sin controladores de excepciones o que contiene los controladores de excepciones que se declaran con [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> No está disponible en ml64.exe.|  
|**/SF**|Agrega el archivo de lista a la lista de como primer paso.|  
|**/SL** `width`|Establece el ancho de línea del origen de lista de caracteres por línea. Intervalo es 60 a 255 o 0. Valor predeterminado es 0. Igual que [página](../../assembler/masm/page.md) ancho.|  
|**/Sn**|Desactiva la tabla de símbolos cuando se produzca una lista.|  
|**/SP** `length`|Establece la longitud de la página de lista en las líneas por página de origen. Intervalo es de 10 a 255 o 0. Valor predeterminado es 0. Igual que [página](../../assembler/masm/page.md) longitud.|  
|**/Ss** `text`|Especifica el texto de la lista de origen. Igual que [subtítulo](../../assembler/masm/subtitle.md) texto.|  
|**/ St** `text`|Especifica el título de la lista de origen. Igual que [título](../../assembler/masm/title.md) texto.|  
|**/SX**|Activa condicionales falsas en la lista.|  
|**/TA** `filename`|Ensambla el archivo de origen cuyo nombre no termina con la extensión de ASM.|  
|**/ w**|Igual que **/W0/WX**.|  
|**/ W** `level`|Establece el nivel de advertencia, donde `level` = 0, 1, 2 ó 3.|  
|**/WX**|Devuelve un código de error si se generan advertencias.|  
|**/X**|Omitir la ruta de acceso de entorno INCLUDE.|  
|**/Zd**|Genera información de número de línea en el archivo objeto.|  
|**/ZF**|Hace que todos los símbolos públicos.|  
|**/ Zi**|Genera información de CodeView en el archivo objeto.|  
|**/Zm**|Permite**M510** opción para lograr la máxima compatibilidad con MASM 5.1.<br /><br /> No está disponible en ml64.exe.|  
|**/Zp**[[`alignment`]]|Empaqueta las estructuras en el límite de bytes especificada. La `alignment` puede ser 1, 2 ó 4.|  
|**/Zs**|Realiza una comprobación de sintaxis solo.|  
|**/?**|Muestra un resumen de sintaxis de línea de comandos de ML.|  
  
 `filename`  
 Nombre del archivo.  
  
 `linkoptions`  
 Las opciones de vínculo.  Vea [opciones del vinculador](../../build/reference/linker-options.md) para obtener más información.  
  
## <a name="remarks"></a>Comentarios  
 Algunas opciones de línea de comandos de ML y ML64 son dependientes de la selección de ubicación. Por ejemplo, porque ML y ML64 pueden aceptar varias **/c** opciones, cualquier correspondiente **/Fo** opciones deben especificarse antes **/c**. En el siguiente ejemplo de línea de comandos muestra una especificación de archivo de objeto por cada especificación de archivo de ensamblado:  
  
 **ml.exe/fo a1.obj /c a.asm/fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>Variables de entorno  
  
|Variable|Descripción|  
|--------------|-----------------|  
|INCLUDE|Especifica la ruta de búsqueda de archivos de inclusión.|  
|ML|Especifica las opciones de línea de comandos de forma predeterminada.|  
|TMP|Especifica la ruta de acceso para archivos temporales.|  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de Error de ML](../../assembler/masm/ml-error-messages.md)   
 [Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)