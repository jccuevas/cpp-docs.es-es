---
title: Referencia de la línea de comandos de ML y ML64
description: Guía de referencia de las opciones de línea de comandos de Microsoft MASM ML y ML64 Assembly.
ms.date: 02/09/2020
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
ms.openlocfilehash: b5c5a79417cb141da3d5cfe1c08aa39e02a9c7c2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257369"
---
# <a name="ml-and-ml64-command-line-reference"></a>Referencia de la línea de comandos de ML y ML64

Ensambla y vincula uno o más archivos de código fuente de lenguaje de ensamblado. Las opciones de la línea de comandos distinguen mayúsculas de minúsculas.

Para obtener más información sobre ml64. exe, consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Sintaxis

> ML \[*Opciones*] *nombre de archivo* \[ \[*Opciones*] *nombre de archivo*]
>
> ML64 \[*Opciones*] *nombre de archivo* \[ \[*Opciones*] *nombre de archivo*]... \[/Link *link_options*]

### <a name="parameters"></a>Parámetros

*opciones*\
Las opciones que se muestran en la tabla siguiente.

|Opción|Acción|
|------------|------------|
|**/AT**|Habilita la compatibilidad con el modelo de memoria diminuto. Habilita los mensajes de error para las construcciones de código que infringen los requisitos de los archivos de formato. com. Esta opción no es equivalente a [. ](dot-model.md)Directiva **diminuto** de modelo.<br /><br /> No está disponible en ml64. exe.|
|*Nombre de archivo* /BL|Selecciona un vinculador alternativo.|
|**/c**|Solo ensambla. No realiza ninguna vinculación.|
|**/coff**|Genera el tipo COFF (Common Object File Format) del módulo de objeto. Necesario para el desarrollo del lenguaje de ensamblado Win32.<br /><br /> No está disponible en ml64. exe.|
|**/CP**|Conserva el caso de todos los identificadores de usuario.|
|**/Cu**|Asigna todos los identificadores a mayúsculas (valor predeterminado).<br /><br /> No está disponible en ml64. exe.|
|**CX**|Conserva las mayúsculas y minúsculas en los símbolos Public y extern.|
|**/D** *Symbol*⟦ =*valor*⟧|Define una macro de texto con el nombre especificado. Si falta *Value* , está en blanco. Varios tokens separados por espacios deben ir entre comillas.|
|**/EP**|Genera una lista de origen preprocesada (enviada a STDOUT). Vea **/SF**.|
|**/errorreport** [ **ninguno** &#124; **-solicitar** &#124; **envío** de **cola** &#124; ]| En desuso. Los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|**/F** *hexnum*|Establece el tamaño de la pila en *hexnum* bytes (igual que **/Link/Stack**:*Number*). El valor debe expresarse en notación hexadecimal. Debe haber un espacio entre **/f** y *hexnum*.|
|**/Fe** *nombreDeArchivo*|Asigna un nombre al archivo ejecutable.|
|**/FL**⟦*nombrearchivo*⟧|Genera una lista de código ensamblado. Vea **/SF**.|
|**/FM**⟦*nombrearchivo*⟧|Crea un archivo de mapa del enlazador.|
|**/FO** *nombreDeArchivo*|Asigna un nombre a un archivo objeto. Para obtener más información, vea [Comentarios](#remarks).|
|**/FPi**|Genera correcciones del emulador para la aritmética de punto flotante (solo en lenguaje mixto).<br /><br /> No está disponible en ml64. exe.|
|**/Fr**⟦*nombrearchivo*⟧|Genera un archivo. SBR del explorador de código fuente.|
|**/Fr**⟦*nombrearchivo*⟧|Genera una forma extendida de un archivo. SBR del explorador de código fuente.|
|**/GC**|Especifica el uso de las convenciones de nomenclatura y llamada a funciones de estilo FORTRAN o Pascal. Igual que el **lenguaje de opciones: Pascal**.<br /><br /> No está disponible en ml64. exe.|
|**/Gd**|Especifica el uso de la llamada de función de estilo C y las convenciones de nomenclatura. Igual que el **lenguaje de opciones: C**.<br /><br /> No está disponible en ml64. exe.|
|**/GZ**|Especifica el uso de llamadas a funciones de __stdcall y convenciones de nomenclatura.  Igual que el **lenguaje de opciones: STCALL**.<br /><br /> No está disponible en ml64. exe.|
|*Número* de/h|Restringe los nombres externos para numerar caracteres significativos. El valor predeterminado es 31 caracteres.<br /><br /> No está disponible en ml64. exe.|
|**/help**|Llama a QuickHelp para obtener ayuda sobre ML.|
|**/I** *nombreruta*|Establece la ruta de acceso del archivo de inclusión. Se permite un máximo de 10 opciones **/i** .|
|**/nologo**|Suprime los mensajes para el ensamblado correcto.|
|**/OMF**|Genera el tipo de formato de archivo de módulo de objetos (OMF) del módulo de objeto.  **/OMF** implica **/c**; ML. exe no admite la vinculación de objetos OMF.<br /><br /> No está disponible en ml64. exe.|
|**/SA**|Activa la lista de toda la información disponible.|
|**/SAFESEH**|Marca el objeto como que no contiene ningún controlador de excepciones o que contiene controladores de excepciones que se declaran con [. SAFESEH](dot-safeseh.md).<br /><br /> No está disponible en ml64. exe.|
|**/Sf**|Agrega una lista de primer paso al archivo de lista.|
|*Ancho* de/SL|Establece el ancho de línea de la lista de origen en caracteres por línea. El intervalo es de 60 a 255 o 0. El valor predeterminado es 0. Igual que el ancho de [Página](page.md) .|
|**/SN**|Desactiva la tabla de símbolos cuando se genera una lista.|
|*Longitud* de/SP|Establece la longitud de la página de la lista de origen en líneas por página. El intervalo es de 10 a 255 o 0. El valor predeterminado es 0. Igual que la longitud de la [Página](page.md) .|
|**/SS** ( *texto* )|Especifica el texto para la lista de código fuente. Igual que el texto del [subtítulo](subtitle.md) .|
|**/St** ( *texto* )|Especifica el título de la lista de origen. Igual que el texto del [título](title.md) .|
|**/Sx**|Activa la enumeración de los condicionales falsos.|
|*Nombre de archivo* /TA|Ensambla el archivo de código fuente cuyo nombre no termina con la extensión. asm.|
|**/w**|Igual que **/W0/WX**.|
|*Nivel* /w|Establece el nivel de advertencia, donde *LEVEL* = 0, 1, 2 o 3.|
|**/WX**|Devuelve un código de error si se generan advertencias.|
|**/X**|Omitir incluir ruta de acceso del entorno.|
|**/Zd**|Genera información de números de línea en el archivo objeto.|
|**/ZF**|Hace que todos los símbolos sean públicos.|
|**/Zi**|Genera información de CodeView en el archivo objeto.|
|**/Zm**|Habilita la opción**M510** para obtener la máxima compatibilidad con MASM 5,1.<br /><br /> No está disponible en ml64. exe.|
|**/ZP**⟦*alignment*⟧|Empaqueta las estructuras en el límite de bytes especificado. La *alineación* puede ser 1, 2 ó 4.|
|**/Zs**|Solo realiza una comprobación de sintaxis.|
|**/?**|Muestra un resumen de la sintaxis de línea de comandos de ML.|

*nombre de archivo*\
Nombre del archivo.

*link_options*\
Opciones de vínculo. Para obtener más información, vea [Opciones del enlazador](../../build/reference/linker-options.md).

## <a name="remarks"></a>Observaciones

Algunas opciones de la línea de comandos de ML y ML64 son sensibles a la selección de ubicación. Por ejemplo, como ML y ML64 pueden aceptar varias opciones de **/c** , se deben especificar las opciones **/FO** correspondientes antes de **/c**. El siguiente ejemplo de línea de comandos muestra una especificación de archivo objeto para cada especificación de archivo de ensamblado:

```cmd
ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm
```

## <a name="environment-variables"></a>Variables de entorno

|Variable|Descripción|
|--------------|-----------------|
|INCLUDE|Especifica la ruta de búsqueda para los archivos de inclusión.|
|ML|Especifica las opciones predeterminadas de la línea de comandos.|
|GESTIÓN|Especifica la ruta de acceso de los archivos temporales.|

## <a name="see-also"></a>Consulte también

[Mensajes de error de ML](ml-error-messages.md)\
[Referencia de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)
