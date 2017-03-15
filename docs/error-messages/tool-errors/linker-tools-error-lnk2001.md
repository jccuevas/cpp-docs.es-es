---
title: Herramientas del vinculador LNK2001 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 3629075e5659cb89ab751b011f3ce2cbf89397cc
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2001"></a>Error de las herramientas del vinculador LNK2001
símbolo externo sin resolver "symbol"  
  
 Código hace referencia a algo (por ejemplo, una función, variable o etiqueta) que el vinculador no puede encontrar en las bibliotecas y archivos objeto.  
  
 Este mensaje de error va seguido de un error grave [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md).  
  
 **Causas posibles**  
  
-   Cuando se actualiza una biblioteca administrada o un proyecto de servicio web desde Visual C++ 2003, la **/Zl** opción del compilador se agrega a la **línea de comandos** página de propiedades. Esto produce el error LNK2001.  
  
     Para resolver este error, agregue msvcrt.lib y msvcmrt.lib a la propiedad dependencias adicionales del vinculador. O bien, quite **/Zl** desde el **línea de comandos** página de propiedades. Para obtener más información, consulte [/Zl (omitir nombre de biblioteca predeterminado)](../../build/reference/zl-omit-default-library-name.md) y [trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).  
  
-   Lo que el código pide no existe (el símbolo está mal escrito o utiliza el formato erróneo, por ejemplo).  
  
-   El código pide algo equivocado (que está utilizando distintas versiones de las bibliotecas, unas de una versión de producto y otras de otra versión).  
  
 **Causas específicas**  
  
 **Problemas de codificación**  
  
-   Si el texto de diagnóstico LNK2001 notifica que `__check_commonlanguageruntime_version` es un símbolo externo sin resolver, consulte [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) para obtener información sobre cómo resolverlo.  
  
-   La definición de plantilla de miembro está fuera de la clase. Visual C++ tiene una limitación en el que las plantillas de miembro deben estar completamente definidas dentro de la clase envolvente. Consulte el artículo KB Q239436 para obtener más información acerca de las plantillas de miembro y el error LNK2001.  
  
-   Caso de error de coincidencia en el código o la definición de módulo (.def) archivos pueden generar el error LNK2001. Por ejemplo, si una variable se ha denominado `var1` en un C++ archivo de origen y ha intentado obtener acceso a él como `VAR1` en otro.  
  
-   Un proyecto que usa [inclusión de funciones](../../error-messages/tool-errors/function-inlining-problems.md) pero defina las funciones en un archivo .cpp en lugar de en el encabezado de archivo puede generar el error LNK2001.  
  
-   Llamar a una función de C desde un programa de C++ sin usar `extern` "C" (lo que hace que el compilador use la convención de nomenclatura de C) puede generar el error LNK2001. Opciones del compilador [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) y [TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) que el compilador compile los archivos como C++ o C, respectivamente, independientemente de la extensión de nombre de archivo. Estas opciones pueden dar lugar a nombres de función diferentes de lo esperado.  
  
-   Intentar hacer referencia a funciones o datos que no tienen vinculación externa puede generar el error LNK2001. En C++, las funciones inline y `const` datos tienen vinculación interna a menos que se especifiquen explícitamente como `extern`.  
  
-   Un [falta el cuerpo de función o variable](../../error-messages/tool-errors/missing-function-body-or-variable.md) puede generar el error LNK2001. Con un prototipo de función o `extern` declaración el compilador puede continuar sin errores, pero el vinculador no puede resolver una llamada a una dirección o una referencia a una variable porque no hay ningún código de función o variable espacio reservado.  
  
-   Llamar a una función con tipos de parámetro que no coinciden con los de la declaración de función puede generar el error LNK2001. [Decoración de nombres](../../error-messages/tool-errors/name-decoration.md) incorpora los parámetros de una función en el nombre de función representativo final.  
  
-   Incluye prototipos, que hacen que el compilador puede esperar un cuerpo de función que no se proporciona incorrectamente pueden generar el error LNK2001. Si tiene una clase y no de clase de implementación de una función `F`, tenga cuidado con las reglas de resolución de ámbito de C++.  
  
-   Al utilizar C++, incluir un prototipo de función en una definición de clase y no [incluye la implementación](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la función de esa clase puede generar el error LNK2001.  
  
-   Intentando llamar a una función virtual pura desde el constructor o destructor de una clase base abstracta puede generar el error LNK2001. Una función virtual pura tiene ninguna implementación de la clase base.  
  
-   Intentar usar una variable declarada en una función ([una variable local](../../error-messages/tool-errors/automatic-function-scope-variables.md)) fuera del ámbito de esa función puede generar el error LNK2001.  
  
-   Cuando se compila una versión de lanzamiento de un proyecto ATL, indica que se requiere código de inicio de CRT. Para solucionarlo, siga uno de los siguientes  
  
    -   Quitar `_ATL_MIN_CRT` de la lista del preprocesador define que se permita incluir código de inicio CRT. Consulte [página de propiedades de opciones de configuración](../../ide/general-property-page-project.md) para obtener más información.  
  
    -   Si es posible, quite las llamadas a las funciones de CRT que requieren código CRT de inicio. En su lugar, use sus equivalentes Win32. Por ejemplo, utilice `lstrcmp` en lugar de `strcmp`. Las funciones conocidas que requieren código de inicio CRT son parte de la cadena y funciones de punto flotante.  
  
 **Compilar y vincular problemas**  
  
-   El proyecto falta una referencia a una biblioteca (. LIB) o un objeto (. Archivo OBJ). Consulte [archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md) para obtener más información.  
  
-   Si utiliza [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) o [/Zl](../../build/reference/zl-omit-default-library-name.md), las bibliotecas que contienen el código necesario no se vincularán en el proyecto a menos que se hayan incluido explícitamente. (Cuando se compila con **/CLR** o **/CLR: pure**, verá una referencia a .cctor; vea [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) para obtener más información.)  
  
-   Si se utiliza Unicode y MFC, obtendrá una externo sin resolver en `_WinMain@16` si no se crea un punto de entrada a `wWinMainCRTStartup`; utilice la [/Entry](../../build/reference/entry-entry-point-symbol.md). Consulte [resumen de la programación de Unicode](../../text/unicode-programming-summary.md).  
  
     Consulte los siguientes artículos de Knowledge Base, ubicados en la biblioteca de MSDN para obtener más información. En MSDN Library, haga clic en el **búsqueda** ficha, pegue el número de artículo o su título en el cuadro de texto y, a continuación, haga clic en **mostrar temas**. Si busca el número de artículo, asegúrese de que el **buscar sólo títulos** opción está desactivada.  
  
    -   Q125750 "PRB: Error LNK2001: '_WinMain@16': no resuelta símbolo externo"  
  
    -   Q131204 "PRB: selección de proyecto equivocado provoca el error LNK2001 en _WinMain@16"  
  
    -   Q100639 "compatibilidad con Unicode en Microsoft Foundation Class Library"  
  
    -   Q291952 "PRB: vincular el Error LNK2001: símbolo externo sin resolver _main"  
  
-   Vincular código compilado con /MT con la biblioteca LIBC.lib provoca el error LNK2001 en `_beginthread`, `_beginthreadex`, `_endthread`, y `_endthreadex`.  
  
-   Vincular código que requiere las bibliotecas multiproceso (cualquier código MFC o código compilado con [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)) provoca el error LNK2001 en [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md), `_beginthreadex`, [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md), y `_endthreadex`. Consulte el siguiente artículo de Knowledge Base para obtener más información:  
  
    -   Q126646 "PRB: mensaje de Error: error LNK2001 en __beginthreadex y \__endthreadex"  
  
    -   Q128641 "INFO: /Mx opciones del compilador y el LIBC LIBCMT, MSVCRT Libs"  
  
    -   Q166504 "PRB: deben coincidir con MFC y CRT de depuración y lanzamiento y estático o dinámico"  
  
-   Al compilar con **/MD**, una referencia a "func" en el origen se convierte en una referencia "`__imp__func`" en el objeto, ya que ahora se mantiene todo el tiempo de ejecución dentro de un archivo DLL. Si se intenta vincular con las bibliotecas estáticas LIBC.lib o LIBCMT.lib, obtendrá LNK2001 en `__imp__func`. Si se intenta vincular con MSVCxx.lib al compilar sin/MD no siempre obtendrá LNK2001, pero probablemente tendrá otros problemas.  
  
-   Vincular con las bibliotecas de modo de lanzamiento al generar una versión de depuración de una aplicación puede generar el error LNK2001. De forma similar, utilizando un **/Mxd** opción (**/MTd**, o **MDd**) o definir `_DEBUG` y, a continuación, vincular con las bibliotecas de lanzamiento le dará posibles externos sin resolver (entre otros problemas). Vinculación de modo de lanzamiento con las bibliotecas de depuración también causará problemas similares.  
  
-   Mezcla de versiones de las bibliotecas de Microsoft y productos de compiladores puede resultar problemático. Bibliotecas de una nueva versión del compilador pueden contener nuevos símbolos que no se encuentra en las bibliotecas incluidas con versiones anteriores. Puede cambiar el orden de los directorios de la ruta de búsqueda, o cambiarlos para que señale a la versión actual.  
  
     Las herramientas | Opciones | Proyectos | Cuadro de diálogo directorios de VC ++, en la selección de archivos de biblioteca, permite cambiar el orden de búsqueda. La carpeta vinculador del cuadro de diálogo páginas de propiedades del proyecto también puede contener rutas de acceso que podrían no estar actualizados.  
  
     Este problema puede aparecer cuando se instala un nuevo SDK (quizás en una ubicación diferente), y el orden de búsqueda no se actualiza para señalar a la nueva ubicación. Normalmente, se debe colocar la ruta de acceso a los nuevos SDK include y lib directorios delante de la ubicación predeterminada de Visual C++. Además, todavía puede indicar si un proyecto contiene rutas de acceso incrustadas rutas antiguas que son válidos pero actualizada para la nueva funcionalidad agregada por la nueva versión que se instala en una ubicación diferente.  
  
-   Actualmente no hay ningún estándar para [nomenclatura C++](../../error-messages/tool-errors/name-decoration.md) entre fabricantes de compiladores, ni entre versiones diferentes de un compilador. Por lo tanto, vincular archivos objeto compilados con otros compiladores puede no producir el mismo esquema de nomenclatura y esto provocará el error LNK2001.  
  
-   [Opciones de compilación de mezcla en línea y no en línea](../../error-messages/tool-errors/function-inlining-problems.md) en módulos diferentes puede causar el error LNK2001. Si se crea una biblioteca de C++ con la inclusión de funciones activada (**/Ob1** o **/Ob2**), pero el archivo de encabezado correspondiente que describe las funciones tiene desactivada (no `inline` palabra clave), obtendrá este error. Para evitar este problema, las funciones inline definieron con `inline` en el archivo de encabezado que se va a incluir en otros archivos.  
  
-   Si está utilizando la `#pragma inline_depth` compilador la directiva, asegúrese de tener un [establecer valor de 2 o mayor](../../error-messages/tool-errors/function-inlining-problems.md)y asegúrese de que está utilizando el [/Ob1](../../build/reference/ob-inline-function-expansion.md) o [/Ob2](../../build/reference/ob-inline-function-expansion.md) opción del compilador.  
  
-   Omitir la opción de LINK /NOENTRY al crear un archivo DLL sólo de recursos causará el error LNK2001.  
  
-   Usar una configuración incorrecta de /SUBSYSTEM o /ENTRY puede generar el error LNK2001. Por ejemplo, si escribe una aplicación basada en caracteres (una aplicación de consola) y especifica/SUBSYSTEM: Windows, obtendrá un externo sin resolver para `WinMain`. Para obtener más información sobre estas opciones y puntos de entrada, consulte la [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) y [/Entry](../../build/reference/entry-entry-point-symbol.md) opciones del vinculador.  
  
 **Problemas de exportación**  
  
-   Al convertir una aplicación de 16 a 32 ó 64 bits, se puede generar el error LNK2001. La sintaxis actual de archivo de definición de módulos (.def) requiere que `__cdecl`, `__stdcall`, y `__fastcall` funciones se muestran en la sección EXPORTS sin subrayados (sin decorar). Esto difiere de la sintaxis de 16 bits, donde debe aparecer con subrayados (decoradas). Para obtener más información, vea la descripción de la [exportaciones](../../build/reference/exports.md) sección de archivos de definición de módulo.  
  
-   Cualquier exportación enumerados en el archivo .def y no encuentra produce el error LNK2001. Esto podría deberse a que no existe, está escrito incorrectamente o usa nombres representativos de C++ (los archivos .def no toman nombres representativos)  
  
 **Interpretar la salida**  
  
 Cuando un símbolo está sin resolver, puede obtener información acerca de la función por las siguientes directrices:  
  
 En x86 plataformas, la decoración de convención de llamada para los nombres compilan en C o para extern "C" nombres en C++, es:  
  
 `__cdecl`  
 Función tiene un prefijo de subrayado (_).  
  
 `__stdcall`  
 Función tiene un prefijo de subrayado (_) y un sufijo @ seguido por el valor dword tamaño alineado de los parámetros de la pila.  
  
 `__fastcall`  
 Función tiene un prefijo @ y un sufijo @ seguido por el valor dword tamaño alineado de los parámetros de la pila.  
  
 Use undname.exe para obtener la forma no decorada de un nombre representativo.  
  
 Para obtener más información sobre algunas de las causas enumeradas anteriormente, consulte [nombre decoración](../../error-messages/tool-errors/name-decoration.md).
