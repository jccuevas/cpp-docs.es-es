---
title: Error de las herramientas del enlazador LNK2001
ms.date: 12/19/2019
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: b6d1e53d8f057ddc93e2dfde65cb951d247dfcc0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302138"
---
# <a name="linker-tools-error-lnk2001"></a>Error de las herramientas del enlazador LNK2001

> símbolo externo sin resolver "*Symbol*"

El código compilado realiza una referencia o una llamada a *Symbol*. El símbolo no está definido en ninguna biblioteca o archivo objeto buscado por el enlazador.

Este mensaje de error va seguido de un error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Para corregir el error LNK1120, primero Corrija todos los errores LNK2001 y LNK2019.

Hay muchas maneras de obtener errores LNK2001. Todos ellos incluyen una *referencia* a una función o variable que el vinculador no puede *resolver*o buscar una definición para. El compilador puede identificar si el código no *declara* un símbolo, pero no cuando no se *define* uno. Esto se debe a que la definición puede estar en un archivo o biblioteca de origen diferente. Si el código hace referencia a un símbolo, pero nunca se define, el vinculador genera un error.

## <a name="what-is-an-unresolved-external-symbol"></a>¿Qué es un símbolo externo sin resolver?

Un *símbolo* es el nombre interno de una función o una variable global. Es el formato del nombre usado o definido en un archivo o biblioteca de objetos compilados. Se define una variable global en el archivo objeto en el que se asigna el almacenamiento. Una función se define en el archivo objeto donde se coloca el código compilado para el cuerpo de la función. Se hace referencia a un *símbolo externo* en un archivo objeto, pero se define en otro archivo de biblioteca u objeto. Un *símbolo exportado* es aquél que está disponible públicamente por el archivo objeto o la biblioteca que lo define.

Para crear una aplicación o un archivo DLL, cada símbolo usado debe tener una definición. El enlazador debe *resolver*o encontrar la definición coincidente para, cada uno de los símbolos externos a los que hace referencia cada archivo objeto. El vinculador genera un error cuando no puede resolver un símbolo externo. Significa que el enlazador no pudo encontrar una definición de símbolo exportado coincidente en ninguno de los archivos vinculados.

## <a name="compilation-and-link-issues"></a>Problemas de compilación y vinculación

Este error puede producirse:

- Cuando el proyecto no tiene una referencia a una biblioteca (. LIB) u Object (. OBJ). Para corregir este problema, agregue al proyecto una referencia a la biblioteca o archivo de objeto requerido. Para obtener más información, vea [archivos lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).

- Cuando el proyecto tiene una referencia a una biblioteca (. LIB) u Object (. OBJ) que a su vez requiere símbolos de otra biblioteca. Puede ocurrir incluso si no llama a funciones que causan la dependencia. Para corregir este problema, agregue una referencia a la otra biblioteca a su proyecto. Para obtener más información, consulte [Descripción del modelo clásico para la vinculación: toma de símbolos para la conducción](https://devblogs.microsoft.com/oldnewthing/20130108-00/?p=5623).

- Si usa las opciones [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) o [/ZL](../../build/reference/zl-omit-default-library-name.md) . Cuando se especifican estas opciones, las bibliotecas que contienen código necesario no se vinculan al proyecto a menos que se hayan incluido explícitamente. Para corregir este problema, incluya explícitamente todas las bibliotecas que use en la línea de comandos de vínculo. Si ve muchos nombres de funciones de biblioteca estándar o CRT que faltan al usar estas opciones, incluya explícitamente los archivos dll de la biblioteca CRT y estándar o los archivos de biblioteca en el vínculo.

- Si se compila con la opción **/CLR** . Puede que falte una referencia a `.cctor`. Para obtener más información sobre cómo corregir este problema, vea [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).

- Si se vincula a las bibliotecas de modo de versión al compilar una versión de depuración de una aplicación. Del mismo modo, si usa las opciones **/MTD** o **/mdd** o define `_DEBUG` y, a continuación, vincula a las bibliotecas de versión, debe esperar muchos externos potenciales sin resolver, entre otros problemas. La vinculación de una compilación de modo de versión con las bibliotecas de depuración también causa problemas similares. Para corregir este problema, asegúrese de que usa las bibliotecas de depuración en las compilaciones de depuración y las bibliotecas comerciales en las compilaciones comerciales.

- Si el código hace referencia a un símbolo de una versión de la biblioteca, pero vincula una versión diferente de la biblioteca. Por lo general, no se pueden combinar archivos objeto o bibliotecas que se compilan para versiones diferentes del compilador. Las bibliotecas que se incluyen en una versión pueden contener símbolos que no se encuentran en las bibliotecas incluidas en otras versiones. Para solucionar este problema, compile todos los archivos de objeto y bibliotecas con la misma versión del compilador antes de vincularlos. Para obtener más información, consulte [ C++ compatibilidad binaria 2015-2019](../../porting/binary-compat-2015-2017.md).

- Si las rutas de acceso de la biblioteca no están actualizadas. Las **herramientas > opciones > proyectos > cuadro de diálogo directorios de VC + +** , en la selección **archivos de biblioteca** , permite cambiar el orden de búsqueda de la biblioteca. La carpeta del vinculador en el cuadro de diálogo páginas de propiedades del proyecto también puede contener rutas de acceso que no estén actualizadas.

- Cuando se instala un nuevo Windows SDK (quizás en una ubicación diferente). El orden de búsqueda de la biblioteca debe actualizarse para que apunte a la nueva ubicación. Normalmente, debe colocar la ruta de acceso en los directorios de inclusión y de biblioteca de SDK nuevos delante C++ de la ubicación visual predeterminada. Además, un proyecto que contenga rutas de acceso incrustadas puede seguir señalando a rutas de acceso anteriores que sean válidas pero no estén actualizadas. Actualice las rutas de acceso para la nueva funcionalidad agregada por la nueva versión que se instala en una ubicación diferente.

- Si compila en la línea de comandos y ha creado sus propias variables de entorno. Compruebe que las rutas de acceso a las herramientas, bibliotecas y archivos de encabezado van a una versión coherente. Para obtener más información, vea [establecer la ruta de acceso y las variables de entorno para las compilaciones de línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

## <a name="coding-issues"></a>Problemas de codificación

Este error puede deberse a:

- No coinciden las mayúsculas y minúsculas en el código fuente o el archivo de definición de módulo (. def). Por ejemplo, si se denomina una variable `var1` en un C++ archivo de código fuente e intenta tener acceso a ella como `VAR1` en otro, se genera este error. Para corregir este problema, use nombres escritos con mayúsculas y minúsculas de forma coherente.

- Proyecto que usa la [inclusión de funciones](../../error-messages/tool-errors/function-inlining-problems.md). Puede producirse al definir las funciones como `inline` en un archivo de código fuente, en lugar de en un archivo de encabezado. Las funciones insertadas no se pueden observar fuera del archivo de código fuente que las define. Para corregir este problema, defina las funciones insertadas en los encabezados en los que se declaran.

- Llamar a una función de C C++ desde un programa sin usar una declaración de `extern "C"` para la función de c. El compilador usa convenciones de nomenclatura de símbolos internas C++ diferentes para C y el código. El nombre de símbolo interno es lo que el enlazador busca al resolver símbolos. Para corregir este problema, utilice un contenedor de `extern "C"` en torno a todas las declaraciones de las funciones C++ de c usadas en el código, lo que hace que el compilador use la Convención de nomenclatura interna de c para esos símbolos. Las opciones del compilador [/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) y [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) hacen que el C++ compilador compile archivos como o C, respectivamente, independientemente de cuál sea la extensión del nombre de archivo. Estas opciones pueden hacer que los nombres de función internos sean distintos de los esperados.

- Intento de hacer referencia a funciones o datos que no tienen vinculación externa. En C++, las funciones insertadas y los datos de `const` tienen vinculación interna, a menos que se especifique explícitamente como `extern`. Para corregir este problema, use declaraciones de `extern` explícitas en símbolos a los que se hace referencia fuera del archivo de código fuente de definición.

- Una definición de [variable o cuerpo de función que falta](../../error-messages/tool-errors/missing-function-body-or-variable.md) . Este error es habitual cuando se declaran, pero no se definen, variables, funciones o clases en el código. El compilador solo necesita un prototipo de función o `extern` declaración de variable para generar un archivo objeto sin errores, pero el enlazador no puede resolver una llamada a la función o una referencia a la variable porque no hay código de función o espacio de variables reservado. Para corregir este problema, asegúrese de definir todas las funciones y variables a las que se hace referencia en un archivo o biblioteca de origen que vincule.

- Una llamada de función que usa tipos de valor devuelto y parámetro, o convenciones de llamada que no coinciden con las de la definición de función. En C++ los archivos objeto, la [decoración de nombres](../../error-messages/tool-errors/name-decoration.md) codifica la Convención de llamada, el ámbito de clase o espacio de nombres y los tipos de valor devuelto y parámetro de una función. La cadena codificada pasa a formar parte del nombre de función representativo final. El enlazador usa este nombre para resolver o hacer coincidir llamadas a la función desde otros archivos objeto. Para corregir este problema, asegúrese de que la declaración de la función, la definición y las llamadas utilizan los mismos ámbitos, tipos y convenciones de llamada.

- C++código al que se llama cuando se incluye un prototipo de función en una definición de clase, pero no se [incluye la implementación](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la función. Para corregir este problema, asegúrese de proporcionar una definición para todos los miembros de clase a los que llame.

- Intento de llamar a una función virtual pura desde una clase base abstracta. Una función virtual pura no tiene ninguna implementación de clase base. Para corregir este problema, asegúrese de que se han implementado todas las funciones virtuales llamadas.

- Se está intentando usar una variable declarada dentro de una función ([una variable local](../../error-messages/tool-errors/automatic-function-scope-variables.md)) fuera del ámbito de esa función. Para corregir este problema, quite la referencia a la variable que no está en el ámbito o mueva la variable a un ámbito superior.

- Al compilar una versión de lanzamiento de un proyecto ATL, que genera un mensaje que indica que se requiere código de inicio de CRT. Para corregir este problema, realice una de las siguientes acciones:

  - Quite `_ATL_MIN_CRT` de la lista de definiciones del preprocesador para permitir que se incluya código de inicio de CRT. Para obtener más información, vea [Página de propiedades general (proyecto)](../../build/reference/general-property-page-project.md).

  - Si es posible, quite las llamadas a funciones de CRT que requieran código de inicio de CRT. En su lugar, use sus equivalentes de Win32. Por ejemplo, use `lstrcmp` en lugar de `strcmp`. Las funciones conocidas que requieren código de inicio de CRT son algunas de las funciones de cadena y de punto flotante.

## <a name="consistency-issues"></a>Problemas de coherencia

Actualmente no hay ningún estándar para la [ C++ decoración de nombres](../../error-messages/tool-errors/name-decoration.md) entre los proveedores de compiladores, ni siquiera entre las distintas versiones del mismo compilador. Los archivos objeto compilados con distintos compiladores no pueden usar el mismo esquema de nomenclatura. La vinculación puede producir el error LNK2001.

La [combinación de opciones de compilación alineadas y no alineadas](../../error-messages/tool-errors/function-inlining-problems.md) en módulos diferentes puede producir el error LNK2001. Si una C++ biblioteca se crea con la inserción de funciones activada ( **/ob1** o **/OB2**), pero el archivo de encabezado correspondiente que describe las funciones tiene la inserción desactivada (no `inline` palabra clave), se produce este error. Para corregir este problema, defina las funciones `inline` en el archivo de encabezado que se incluye en otros archivos de código fuente.

Si usa la Directiva de compilador de `#pragma inline_depth`, asegúrese de que ha establecido un [valor de 2 o superior](../../error-messages/tool-errors/function-inlining-problems.md)y asegúrese de usar también la opción del compilador [/ob1](../../build/reference/ob-inline-function-expansion.md) o [/OB2](../../build/reference/ob-inline-function-expansion.md) .

Este error puede producirse si se omite la opción de vínculo/NOENTRY al crear un archivo DLL de solo recursos. Para corregir este problema, agregue la opción/NOENTRY al comando Link.

Este error puede producirse si se usa una configuración/SUBSYSTEM o/ENTRY incorrecta en el proyecto. Por ejemplo, si escribe una aplicación de consola y especifica/SUBSYSTEM: WINDOWS, se genera un error externo sin resolver para `WinMain`. Para corregir este problema, asegúrese de que coincide con las opciones del tipo de proyecto. Para obtener más información sobre estas opciones y los puntos de entrada, vea las opciones del vinculador [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) y [/entry](../../build/reference/entry-entry-point-symbol.md) .

## <a name="exported-def-file-symbol-issues"></a>Problemas de símbolos de archivos. def exportados

Este error se produce cuando no se encuentra una exportación enumerada en un archivo. def. Podría deberse a que la exportación no existe, está escrita incorrectamente o usa C++ nombres representativos. Un archivo. def no toma nombres representativos. Para corregir este problema, quite las exportaciones innecesarias y use declaraciones de `extern "C"` para los símbolos exportados.

## <a name="use-the-decorated-name-to-find-the-error"></a>Usar el nombre representativo para encontrar el error

El C++ compilador y el vinculador usan la [decoración de nombres](../../error-messages/tool-errors/name-decoration.md), también conocida como *"cambio de nombre"* . La decoración de nombres codifica información adicional sobre el tipo de una variable en su nombre de símbolo. El nombre de símbolo de una función codifica su tipo de valor devuelto, los tipos de parámetro, el ámbito y la Convención de llamada. Este nombre representativo es el nombre del símbolo que el enlazador busca para resolver los símbolos externos.

Se puede producir un error de vínculo si la declaración de una función o variable no coincide *exactamente* con la definición de la función o variable. Esto se debe a que cualquier diferencia pasa a formar parte del nombre del símbolo para que coincida. El error puede producirse incluso si se usa el mismo archivo de encabezado tanto en el código de llamada como en el código de definición. Una forma de hacerlo es si se compilan los archivos de código fuente con diferentes marcadores de compilador. Por ejemplo, si el código se compila para usar la Convención de llamada `__vectorcall`, pero se vincula a una biblioteca que espera que los clientes la llamen mediante la `__cdecl` predeterminada o `__fastcall` Convención de llamada. En este caso, los símbolos no coinciden porque las convenciones de llamada son diferentes.

Para que le resulte más fácil encontrar la causa, el mensaje de error muestra dos versiones del nombre. Muestra el "nombre descriptivo", el nombre usado en el código fuente y el nombre representativo (entre paréntesis). No es necesario saber cómo interpretar el nombre representativo. Todavía puede buscar y compararlo con otros nombres representativos. Las herramientas de línea de comandos pueden ayudarle a buscar y comparar el nombre de símbolo esperado y el nombre de símbolo real:

- Las opciones [/Exports](../../build/reference/dash-exports.md) y [/Symbols](../../build/reference/symbols.md) de la herramienta de línea de comandos DUMPBIN son útiles aquí. Pueden ayudarle a detectar qué símbolos se definen en los archivos. dll y de objeto o biblioteca. Puede usar la lista de símbolos para comprobar que los nombres representativos exportados coinciden con los nombres representativos que busca el enlazador.

- En algunos casos, el vinculador solo puede informar del nombre representativo de un símbolo. Puede usar la herramienta de línea de comandos UNDNAME para obtener la forma no representativa de un nombre representativo.

## <a name="additional-resources"></a>Recursos adicionales

Para obtener más información, vea la pregunta Stack Overflow ["¿Qué es un error de referencia sin definir o de símbolo externo sin resolver?"](https://stackoverflow.com/q/12573816/2002113).
