---
title: Referencia de la línea de comandos de ML y ML64
ms.date: 08/30/2018
f1_keywords:
- ML
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
ms.openlocfilehash: 64d56ea5eb29162e65782998e91fc1ff70cbf73b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430230"
---
# <a name="ml-and-ml64-command-line-reference"></a>Referencia de la línea de comandos de ML y ML64

Ensambla y se proporcionan vínculos a uno o varios archivos de código fuente del lenguaje de ensamblado. Las opciones de línea de comandos distinguen mayúsculas de minúsculas.

Para obtener más información sobre ml64.exe, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Sintaxis

> ML [[*opciones*]] *filename* [[[[*opciones*]] *filename*]]

> Ml64 [[*opciones*]] *filename* [[[[*opciones*]] *filename*]]... [[/ link *linkoptions*]]

### <a name="parameters"></a>Parámetros

*options*<br/>
Las opciones enumeradas en la tabla siguiente.

|Opción|Acción|
|------------|------------|
|**/AT**|Habilita la compatibilidad del modelo de memoria pequeña. Permite que los mensajes de error para las construcciones de código que infringen los requisitos para los archivos de formato .com. Tenga en cuenta que esto no es equivalente a la [. MODELO](../../assembler/masm/dot-model.md) **MINÚSCULO** directiva.<br /><br /> No está disponible en ml64.exe.|
|**/BL** *nombre de archivo*|Selecciona a un vinculador alternativo.|
|**/c**|Ensambla solo. No se vincula.|
|**s/COFF**|Genera el tipo de formato (COFF) común de archivo objeto de módulo de objeto. Suelen ser necesarios para desarrollo de lenguaje de ensamblado de Win32.<br /><br /> No está disponible en ml64.exe.|
|**/CP**|Conserva el caso de todos los identificadores de usuario.|
|**/Cu**|Asigna todos los identificadores en mayúsculas (valor predeterminado).<br /><br /> No está disponible en ml64.exe.|
|**/CX**|Mantiene las mayúsculas en los símbolos públicos y extern.|
|**/D** *símbolo*[[=*valor*]]|Define una macro de texto con el nombre especificado. Si *valor* es falta, está en blanco. Varios tokens separados por espacios deben incluirse entre comillas.|
|**/EP**|Genera una lista de código fuente preprocesado (que se envía a STDOUT). Consulte **/Sf**.|
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **PROMPT** &AMP;#124; **COLA** &AMP;#124; **ENVIAR** ]|Si ml.exe o ml64.exe produce un error en tiempo de ejecución, puede usar **/errorreport** para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información acerca de **/errorreport**, consulte [/errorReport (informar de errores de compilador interno)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Conjuntos de tamaño de la pila *hexnum* bytes (Esto equivale a **/vínculo/pila**:*número*). El valor debe expresarse en notación hexadecimal. Debe haber un espacio entre **/F** y *hexnum*.|
|**/Fe** *nombre de archivo*|Nombres de archivo ejecutable.|
|**/Fl**[[*filename*]]|Genera una lista de ensamblados de código. Consulte **/Sf**.|
|**/FM**[[*filename*]]|Crea un archivo de asignación del vinculador.|
|**/Fo** *nombre de archivo*|Nombres de un archivo de objeto. Para obtener más información, vea la sección Comentarios.|
|**/Fpi**|Genera el emulador corrección para la aritmética de punto flotante (solo lenguaje mixto).<br /><br /> No está disponible en ml64.exe.|
|**/FR**[[*filename*]]|Genera un archivo .sbr de explorador de código fuente.|
|**/FR**[[*filename*]]|Genera un formulario extendido de un archivo .sbr de explorador de origen.|
|**/GC**|Especifica el uso de la función de estilo de Pascal o FORTRAN llamando y convenciones de nomenclatura. Igual que **opción LANGUAGE: PASCAL**.<br /><br /> No está disponible en ml64.exe.|
|**/Gd**|Especifica el uso de la función de estilo C llamando y convenciones de nomenclatura. Igual que **opción LANGUAGE: C**.<br /><br /> No está disponible en ml64.exe.|
|**/GZ**|Especifica el uso de la función de __stdcall llamando y convenciones de nomenclatura.  Igual que **opción LANGUAGE: STCALL**.<br /><br /> No está disponible en ml64.exe.|
|**/H** *número*|Restringe los nombres externos al número de caracteres significativo. El valor predeterminado es 31 caracteres.<br /><br /> No está disponible en ml64.exe.|
|**/help**|Llama a QuickHelp para obtener ayuda sobre aprendizaje automático.|
|**/I** *pathname*|Ruta de acceso de conjuntos de archivo de inclusión. Un máximo de 10 **/I** se permiten las opciones.|
|**/nologo**|Suprime los mensajes para el ensamblado correcto.|
|**/OMF**|Genera el tipo de formato (OMF) de archivo de módulo de objeto de módulo de objeto.  **/OMF** implica **/c**; ML.exe no admite la vinculación de objetos OMF.<br /><br /> No está disponible en ml64.exe.|
|**/SA**|Activa la lista de toda la información disponible.|
|**/ SAFESEH**|Marca el objeto como que contiene ningún controlador de excepciones o que contiene los controladores de excepciones que se declaran con [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> No está disponible en ml64.exe.|
|**/SF**|Agrega el archivo de lista a la lista como primer paso.|
|**/SL** *ancho*|Establece el ancho de línea de la lista de caracteres por línea de origen. Intervalo es 60 a 255 o 0. El valor predeterminado es 0. Igual que [página](../../assembler/masm/page.md) ancho.|
|**/Sn**|Desactiva la tabla de símbolos al generar una lista.|
|**/SP** *longitud*|Establece la longitud de la página de lista en las líneas por página de origen. Intervalo es de 10 a 255 o 0. El valor predeterminado es 0. Igual que [página](../../assembler/masm/page.md) longitud.|
|**/Ss** *texto*|Especifica el texto de la lista de origen. Igual que [subtítulo](../../assembler/masm/subtitle.md) texto.|
|**/ST** *texto*|Especifica el título de la lista de origen. Igual que [título](../../assembler/masm/title.md) texto.|
|**/SX**|Enciende condicionales falsas en la lista.|
|**/TA** *nombre de archivo*|Ensambla el archivo de código fuente cuyo nombre no termina con la extensión de ASM.|
|**/w**|Igual que **/W0/WX**.|
|**/W** *nivel*|Establece el nivel de advertencia donde *nivel* = 0, 1, 2 o 3.|
|**/WX**|Devuelve un código de error si se generan advertencias.|
|**/X**|Omitir ruta de acceso de entorno INCLUDE.|
|**/Zd**|Genera información de número de línea en el archivo objeto.|
|**/ZF**|Hace que todos los símbolos públicos.|
|**/Zi**|Genera información de CodeView en el archivo objeto.|
|**/Zm**|Permite**M510** opción para lograr la máxima compatibilidad con MASM 5.1.<br /><br /> No está disponible en ml64.exe.|
|**/Zp**[[*alineación*]]|Empaqueta las estructuras en el límite de bytes especificada. El *alineación* puede ser 1, 2 o 4.|
|**/Zs**|Realiza una comprobación de sintaxis solo.|
|**/?**|Muestra un resumen de sintaxis de línea de comandos de ML.|

*filename*<br/>
Nombre del archivo.

*linkoptions*<br/>
Las opciones de vínculo.  Consulte [opciones del vinculador](../../build/reference/linker-options.md) para obtener más información.

## <a name="remarks"></a>Comentarios

Algunas opciones de línea de comandos de ML y ML64 afectan a la selección de ubicación. Por ejemplo, porque ML y ML64 pueden aceptar varias **/c** opciones, los correspondientes **/Fo** opciones deben especificarse antes **/c**. El siguiente ejemplo de línea de comandos muestra una especificación de archivo de objeto para cada especificación de archivo de ensamblado:

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>Variables de entorno

|Variable|Descripción|
|--------------|-----------------|
|INCLUDE|Especifica la ruta de búsqueda de archivos de inclusión.|
|ML|Especifica las opciones de línea de comandos de forma predeterminada.|
|TMP|Especifica la ruta de acceso para los archivos temporales.|

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>
[Referencia de Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>