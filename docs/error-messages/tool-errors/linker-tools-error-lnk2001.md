---
title: Las herramientas del vinculador LNK2001 Error | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb8e560e46da06c4312ab4261016ccd5a5ddda68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017852"
---
# <a name="linker-tools-error-lnk2001"></a>Error de las herramientas del vinculador LNK2001

símbolo externo sin resolver "*símbolo*"

El código compilado que hace una referencia o una llamada a *símbolos*, pero este símbolo no está definido en cualquiera de las bibliotecas o archivos de objeto especificados al vinculador.

Este mensaje de error va seguido de un error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Debe corregir todos los LNK2001 y LNK2019 errores para corregir el error LNK1120.

## <a name="possible-causes"></a>Causas posibles

Hay muchas maneras de obtener este error, pero todas ellas implican una referencia a una función o variable que el vinculador no *resolver*, o busque una definición. El compilador puede identificar cuándo un símbolo no es *declarado*, pero no cuando no es *definido*, porque la definición puede estar en un archivo de origen diferente o biblioteca. Si se hace referencia a un símbolo, pero nunca se ha definido, el vinculador genera un error.

### <a name="coding-issues"></a>Problemas de codificación

Este error puede deberse a un caso que no coinciden en su código fuente o una definición de módulo (.def) archivo. Por ejemplo, si el nombre de una variable `var1` en un C++ archivo de origen e intente obtener acceso a él como `VAR1` en otra, se genera este error. Para corregir este problema, use sistemáticamente la ortografía y mayúsculas y minúsculas de los nombres de.

Este error puede producirse en un proyecto que usa [inserción de funciones](../../error-messages/tool-errors/function-inlining-problems.md) si define las funciones en un archivo de código fuente en lugar de un archivo de encabezado. Las funciones insertadas no se ve fuera del archivo de origen que los define. Para corregir este problema, defina las funciones insertadas en los encabezados de donde se declaran.

Este error puede producirse si se llama a una función de C desde un programa de C++ sin usar un `extern "C"` declaración para la función. El compilador usa las convenciones de nomenclatura de símbolo interno diferente para el código de C y C++, y es el nombre del símbolo interno que el vinculador busca al resolver los símbolos. Para corregir este problema, use un `extern "C"` contenedor alrededor de todas las declaraciones de funciones de C que se usan en el código de C++, que hace que el compilador use la convención de nomenclatura de C interna para esos símbolos. Opciones del compilador [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) y [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) hará que el compilador compilar archivos como C++ o C, respectivamente, independientemente de la extensión de nombre de archivo. Estas opciones pueden dar lugar a nombres de función interna diferentes de lo esperado.

Este error puede deberse a un intento de hacer referencia a funciones o datos que no tienen vinculación externa. En C++, las funciones insertadas y `const` datos tienen vinculación interna a menos que especifique explícitamente como `extern`. Para corregir este problema, utilice explicit `extern` declaraciones en símbolos contempladas fuera del archivo de origen de definición.

Este error puede deberse a un [falta el cuerpo de función o variable](../../error-messages/tool-errors/missing-function-body-or-variable.md) definición. Este error es habitual cuando se declara, pero no definen, variables, funciones o clases en el código. El compilador sólo necesita un prototipo de función o `extern` declaración de variable para generar un archivo de objeto sin errores, pero el vinculador no puede resolver una llamada a la función o una referencia a la variable porque no hay ningún espacio de variable o el código de función reservado. Para corregir este problema, asegúrese de que cada función que se hace referencia y la variable está totalmente definida en un archivo de origen o la biblioteca que se incluye en el vínculo.

Este error puede deberse a una llamada de función que usa tipos devueltos y parámetros o las convenciones de llamada que no coinciden con los de la definición de función. En los archivos de objeto de C++, [nombre decoración](../../error-messages/tool-errors/name-decoration.md) incorpora la convención de llamada, el ámbito de clase o espacio de nombres y tipos devueltos y parámetros de una función en el nombre de función representativo final, que se usa como el símbolo de coincidirán cuando las llamadas a la función desde otros archivos de objeto se resuelven. Para corregir este problema, asegúrese de que la declaración, definición y llamadas a la función de todos los usan los mismos ámbitos, tipos y las convenciones de llamada.

Este error puede deberse en código de C++ al incluir un prototipo de función en una definición de clase, pero no se pudo [incluyen la implementación](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la función y, a continuación, llamarlo. Para corregir este problema, asegúrese de proporcionar una definición para todos los llama declarado los miembros de una clase.

Este error puede deberse a un intento de llamar a una función virtual pura de una clase base abstracta. Una función virtual pura no tiene ninguna implementación de la clase base. Para corregir este problema, asegúrese de que todos se llama a funciones virtuales se implementan.

Este error puede deberse a que se intenta utilizar una variable declarada dentro de una función ([una variable local](../../error-messages/tool-errors/automatic-function-scope-variables.md)) fuera del ámbito de esa función. Para corregir este problema, quite la referencia a la variable que no está en el ámbito o mover la variable a un ámbito superior.

Este error puede producirse cuando se compila una versión de lanzamiento de un proyecto ATL, generar un mensaje que se requiere código de inicio de CRT. Para solucionar este problema, realice una de las acciones siguientes,

- Quitar `_ATL_MIN_CRT` en la lista del preprocesador define para permitir que el código de inicio de CRT se incluirán. Consulte [página de propiedades General (proyecto)](../../ide/general-property-page-project.md) para obtener más información.

- Si es posible, quite las llamadas a funciones de CRT que requieren código de inicio de CRT. En su lugar, use sus equivalentes de Win32. Por ejemplo, usar `lstrcmp` en lugar de `strcmp`. Las funciones conocidas que requieren código de inicio de CRT son algunas de las cadenas y las funciones de punto flotante.

### <a name="compilation-and-link-issues"></a>Problemas de compilación y vínculo

Este error puede producirse cuando el proyecto no tiene una referencia a una biblioteca (. LIB) o un objeto (. Archivo OBJ). Para corregir este problema, agregue una referencia al archivo de objeto o biblioteca requerida para el proyecto. Para obtener más información, consulte [archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).

Este error puede producirse si usa el [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) o [/Zl](../../build/reference/zl-omit-default-library-name.md) opciones. Al especificar estas opciones, no se vinculan bibliotecas que contienen el código necesario en el proyecto, a menos que se hayan incluido explícitamente. Para corregir este problema, debe incluir explícitamente todas las bibliotecas que se usa en la línea de comandos. Si ve muchos falta CRT o la biblioteca estándar de los nombres de función al usar estas opciones, incluir explícitamente los archivos CRT y archivos DLL de biblioteca estándar o biblioteca en el vínculo.

Si compila con la **/CLR** opción, puede haber una referencia a .cctor que falta. Para corregir este problema, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) para obtener más información.

Este error puede producirse si crea un vínculo a las bibliotecas de modo de versión al compilar una versión de depuración de una aplicación. De forma similar, si utiliza opciones **/MTd** o **/MDd** o definir `_DEBUG` y, a continuación, vincular a las bibliotecas de lanzamiento, debe esperar muchos externos sin resolver posibles, entre otros problemas. Vinculación de un modo de lanzamiento con las bibliotecas de depuración también hace que los problemas similares. Para corregir este problema, asegúrese de que usa las bibliotecas de depuración en las compilaciones de depuración y compila bibliotecas comerciales en su distribuidor.

Este error puede producirse si el código hace referencia a un símbolo de una versión de una biblioteca, pero proporcionar una versión diferente de la biblioteca del vinculador. Por lo general, no se pueden mezclar archivos objeto o bibliotecas que se generan para las diferentes versiones del compilador. Las bibliotecas que se incluyen en una nueva versión pueden contener símbolos que no se encuentra en las bibliotecas incluidas con las versiones anteriores y viceversa. Para corregir este problema, cree todos los archivos objeto y bibliotecas con la misma versión del compilador antes de vincularlas.

-  Las herramientas de &#124; opciones &#124; proyectos &#124; cuadro de diálogo de directorios de VC ++, en la selección de archivos de biblioteca, le permite cambiar el orden de búsqueda de biblioteca. La carpeta vinculador del cuadro de diálogo páginas de propiedades del proyecto también puede contener rutas de acceso que podrían estar obsoletas.

-  Este problema puede aparecer cuando se instala un nuevo SDK (quizás en una ubicación diferente), y el orden de búsqueda no se actualiza para señalar a la nueva ubicación. Normalmente, se debe colocar la ruta de acceso al nuevo SDK include y lib directorios delante de la ubicación predeterminada Visual C++. Además, un proyecto que contiene las rutas de acceso incrustados todavía puede apuntar a rutas de acceso anteriores que sean válidos, pero obsoleto en la nueva funcionalidad agregada por la nueva versión que se instala en una ubicación diferente.

- Si compila en la línea de comandos y ha creado sus propias variables de entorno, compruebe que las rutas de acceso a archivos de encabezado, bibliotecas y herramientas se dirijan a una versión coherente. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

Actualmente no hay ningún estándar para [C++ nomenclatura](../../error-messages/tool-errors/name-decoration.md) entre los proveedores de compiladores, ni entre versiones diferentes de un compilador. Por lo tanto, vincular archivos objeto compilados con otros compiladores puede no producir el mismo esquema de nomenclatura y esto provocará el error LNK2001.

[Opciones de compilación de combinación en línea y no en línea](../../error-messages/tool-errors/function-inlining-problems.md) en módulos diferentes puede causar el error LNK2001. Si se crea una biblioteca de C++ con la inclusión de funciones activado (**/Ob1** o **/Ob2**), pero el archivo de encabezado correspondiente que describe las funciones tiene desactivada (no hay `inline` palabra clave), este error se produce. Para corregir este problema, defina las funciones `inline` en el archivo de encabezado incluido en otros archivos de origen.

Si usas el `#pragma inline_depth` compilador la directiva, asegúrese de tener un [establecer valor de 2 o mayor](../../error-messages/tool-errors/function-inlining-problems.md)y asegúrese también de usar el [/Ob1](../../build/reference/ob-inline-function-expansion.md) o [/Ob2](../../build/reference/ob-inline-function-expansion.md) opción del compilador.

Este error puede producirse si se omite el vínculo de la opción/NOENTRY cuando se crea un archivo DLL de recursos. Para corregir este problema, agregue la opción /NOENTRY al comando de vínculo.

Este error puede producirse si usa /SUBSYSTEM incorrecto o configuración/Entry en el proyecto. Por ejemplo, si escribe una aplicación de consola y especifique/SUBSYSTEM: Windows, se genera un error externo sin resolver para `WinMain`. Para corregir este problema, asegúrese de que coinciden con las opciones para el tipo de proyecto. Para obtener más información sobre estas opciones y puntos de entrada, consulte el [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) y [/Entry](../../build/reference/entry-entry-point-symbol.md) opciones del vinculador.

### <a name="exported-symbol-issues"></a>Problemas de los símbolos exportados

Este error se produce cuando no se encuentra una exportación aparece en un archivo. def. Esto podría deberse a que no existe, está mal escrito o utiliza nombres representativos de C++. Un archivo .def no toman nombres representativos. Para corregir este problema, quite exportaciones innecesarias y usar `extern "C"` declaraciones de los símbolos exportados.

## <a name="what-is-an-unresolved-external-symbol"></a>¿Qué es un símbolo externo sin resolver?

Un *símbolo* es el nombre de una función o variable global que se usa internamente mediante un archivo objeto compilado o biblioteca. Es un símbolo *definido* en el archivo objeto donde se asigna almacenamiento para una variable global o en una función, donde se coloca el código compilado para el cuerpo de función. Un *símbolo externo* es un símbolo que *que se hace referencia*, es decir, usar o llamado en el archivo de un objeto, pero definido en un archivo de biblioteca u objeto diferente. Un *exportar símbolos* es aquella que está disponible públicamente con el archivo objeto o biblioteca que lo define. El vinculador debe *resolver*, o busque la definición coincidente para cada símbolo externo al que hace referencia un archivo objeto cuando se vincula a una aplicación o DLL. El vinculador genera un error cuando no puede resolver un símbolo externo mediante la búsqueda de un símbolo exportado coincidente en cualquiera de los archivos vinculados.

## <a name="use-the-decorated-name-to-find-the-error"></a>Use el nombre representativo para encontrar el error

El uso del compilador y vinculador de C++ [decoración](../../error-messages/tool-errors/name-decoration.md), también conocida como *alteración de nombres*, para codificar información adicional sobre el tipo de una variable o el tipo de valor devuelto, los tipos de parámetro, ámbito y que realiza la llamada convención de una función en el nombre del símbolo. Este nombre representativo es el nombre del símbolo el enlazador busca para resolver los símbolos externos.

Dado que la información adicional se convierte en parte del nombre del símbolo, puede producirse un error de vínculo si la declaración de una función o variable no coinciden exactamente con la definición de la función o variable. Esto puede ocurrir incluso si se utiliza el mismo archivo de encabezado en el código de llamada y el código de definición, si se usan los distintos indicadores de compilador al compilar los archivos de origen. Por ejemplo, puede obtener este error si se compila el código para usar el `__vectorcall` convención de llamada, pero puede vincula a una biblioteca que se espera que los clientes a llamar mediante el valor predeterminado `__cdecl` o `__fastcall` convención de llamada. En este caso, los símbolos no coinciden porque las convenciones de llamada son diferentes

Para ayudarle a encontrar la causa de este tipo de error, el mensaje de error del vinculador muestra tanto el "nombre descriptivo," el nombre usado en el código fuente y el nombre representativo (entre paréntesis) para el símbolo externo sin resolver. No es necesario saber cómo traducir el nombre representativo para poder usarlo compararlo con otros nombres representativos. Puede usar las herramientas de línea de comandos que se incluyen con el compilador para comparar el nombre del símbolo esperado y el nombre del símbolo real:

- El [/EXPORTA](../../build/reference/dash-exports.md) y [/símbolos](../../build/reference/symbols.md) las opciones de la herramienta de línea de comandos DUMPBIN pueden ayudarle a descubrir qué símbolos están definidos en los archivos .dll y biblioteca u objeto. Puede usar esto para comprobar que el representativos exportados nombres coinciden con que los nombres representativos el vinculador busca.

En algunos casos, el vinculador solo puede notificar el nombre representativo para un símbolo. Puede usar la herramienta de línea de comandos UNDNAME para obtener el formato no representativo de un nombre representativo.

## <a name="additional-resources"></a>Recursos adicionales

Para obtener más información sobre las posibles causas y soluciones para el error LNK2001, consulte la pregunta desbordamiento de pila [¿qué es un error de símbolo externo sin definir referencia/unresolved y cómo lo corrijo?](http://stackoverflow.com/q/12573816/2002113).

