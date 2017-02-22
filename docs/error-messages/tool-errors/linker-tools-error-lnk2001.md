---
title: "Error de las herramientas del vinculador LNK2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2001"
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Error de las herramientas del vinculador LNK2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo externo "símbolo" sin resolver  
  
 El código hace referencia a algo \(como una función, variable o etiqueta\) que el vinculador no encuentra en las bibliotecas y archivos objeto.  
  
 Este mensaje de error viene seguido del error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md).  
  
 **Causas posibles**  
  
-   Si se actualiza un proyecto de biblioteca administrada o de servicio Web desde Visual C\+\+ 2003, la opción del compilador **\/Zl** se agrega a la página de propiedades **Línea de comandos**.  Esto produce el error LNK2001.  
  
     Para resolver este error, agregue msvcrt.lib y msvcmrt.lib a la propiedad Dependencias adicionales del vinculador.  O bien, quite **\/Zl** de la página de propiedades **Línea de comandos**.  Para obtener más información, vea [\/Zl \(Omitir nombres de biblioteca predeterminada\)](../../build/reference/zl-omit-default-library-name.md) y [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
-   Lo que el código pide no existe \(el símbolo está mal escrito o no sigue bien las mayúsculas o minúsculas, por ejemplo\).  
  
-   El código pide algo equivocado \(se utilizan versiones mezcladas de las bibliotecas, unas de una versión del producto y otras de otra versión\).  
  
 **Causas específicas**  
  
 **Problemas de código**  
  
-   Si el texto de diagnóstico LNK2001 notifica que `__check_commonlanguageruntime_version` es un símbolo externo sin resolver, vea [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) para obtener información sobre cómo resolverlo.  
  
-   La definición de la plantilla de miembro está fuera de la clase.  En Visual C\+\+, las plantillas de miembro deben definirse por completo en su clase envolvente.  Vea el artículo de KB Q239436 para obtener más información sobre LNK2001 y las plantillas de miembro.  
  
-   Si no coinciden las mayúsculas o minúsculas en el código o en el archivo de definición de módulos \(.def\), se puede generar el error LNK2001.  Por ejemplo, dio a una variable el nombre `var1` en un archivo de código fuente de C\+\+ e intentó obtener acceso a ella como `VAR1` en otro.  
  
-   Un proyecto que utilice [inclusión de funciones en línea](../../error-messages/tool-errors/function-inlining-problems.md), pero defina las funciones en un archivo .cpp en lugar de en el archivo de encabezado, puede generar el error LNK2001.  
  
-   Llamar a una función de C desde un programa de C\+\+ sin usar `extern` "C" \(lo que hace que el compilador use la convención de llamada de C\) también puede causar el error LNK2001.  Las opciones del compilador [\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) y [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) hacen que el compilador compile los archivos como C\+\+ o C respectivamente, independientemente de la extensión del nombre de archivo.  Estas opciones pueden dar lugar a nombres de función diferentes de lo esperado.  
  
-   Intentar hacer referencia a funciones o datos que no poseen vinculación externa puede generar el error LNK2001.  En C\+\+, las funciones inline y los datos `const` poseen vinculación interna a menos que se especifiquen explícitamente como `extern`.  
  
-   Un [cuerpo de función o variable no encontrados](../../error-messages/tool-errors/missing-function-body-or-variable.md) pueden generar el error LNK2001.  Si sólo hay un prototipo de función o declaración `extern`, el compilador puede continuar sin errores, pero el vinculador no puede resolver una llamada a una dirección o una referencia a una variable porque no hay código de función o espacio de variable reservado.  
  
-   Llamar a una función con tipos de parámetros que no coinciden con los de la declaración de función puede generar el error LNK2001.  [Decoración de nombres](../../error-messages/tool-errors/name-decoration.md) incorpora los parámetros de una función en el nombre de función representativo final.  
  
-   Los prototipos incorrectamente incluidos, que hacen que el compilador espere un cuerpo de función no disponible, pueden generar el error LNK2001.  Si hay una implementación de clase y no de clase de una función `F`, debe prestarse atención a las reglas de resolución de ámbito de C\+\+.  
  
-   Al utilizar C\+\+, incluir un prototipo de función en una definición de clase y no [incluir la implementación](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la función de esa clase puede generar el error LNK2001.  
  
-   Intentar llamar a una función virtual pura desde el constructor o destructor de una clase base abstracta puede generar el error LNK2001.  Una función virtual pura no tiene implementación de clase base.  
  
-   Intentar usar una variable declarada dentro de una función \([una variable local](../../error-messages/tool-errors/automatic-function-scope-variables.md)\) fuera del ámbito de esa función puede generar el error LNK2001.  
  
-   Al generar una versión de lanzamiento de un proyecto ATL, el compilador indica que se requiere código de inicio de la biblioteca CRT.  Para resolver el problema, siga uno de los procedimientos siguientes:  
  
    -   Quitar `_ATL_MIN_CRT` de la lista del preprocesador hace que se permita incluir código de inicio CRT.  Vea [página de propiedades Valores de configuración](../../ide/general-property-page-project.md) para obtener más información.  
  
    -   Si es posible, quite las llamadas a funciones CRT que requieren código de inicio CRT.  En su lugar use sus equivalentes Win32.  Por ejemplo, use `lstrcmp` en lugar de `strcmp`.  Entre las funciones conocidas que requieren código de inicio CRT se hallan algunas de las funciones de cadena y punto flotante.  
  
 **Problemas de compilación y vinculación**  
  
-   Falta una referencia a una biblioteca \(.LIB\) o un archivo objeto \(.OBJ\) en el proyecto.  Vea [Archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md) para obtener más información.  
  
-   Si utiliza [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) o [\/Zl](../../build/reference/zl-omit-default-library-name.md), las bibliotecas que contienen el código necesario no se vincularán en el proyecto a menos que las haya incluido explícitamente. \(Al compilar con **\/clr** o **\/clr:pure**, verá una referencia a .cctor; vea [Inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) para obtener más información.\)  
  
-   Si se utiliza Unicode y MFC, se obtendrá un error de símbolo externo sin resolver en `_WinMain@16` si no se crea un punto de entrada a `wWinMainCRTStartup`; debe usarse [\/ENTRY](../../build/reference/entry-entry-point-symbol.md).  Vea [Resumen de la programación con Unicode](../../text/unicode-programming-summary.md).  
  
     Vea los siguientes artículos de Knowledge Base, situados en MSDN Library, para obtener más información.  En MSDN Library, haga clic en la ficha **Buscar**, pegue el número de artículo o su título en el cuadro de texto y haga clic en **Mostrar los temas de Ayuda**.  Si busca por el número de artículo, compruebe que la opción **Buscar en títulos sólo** está desactivada.  
  
    -   Q125750   "PRB: Error LNK2001: '\_WinMain@16': Unresolved External Symbol"  
  
    -   Q131204   "PRB: Wrong Project Selection Causes LNK2001 on \_WinMain@16"  
  
    -   Q100639   "Unicode Support in the Microsoft Foundation Class Library"  
  
    -   Q291952    "PRB: Link Error LNK2001: Unresolved External Symbol \_main"  
  
-   Vincular código compilado con \/MT con la biblioteca LIBC.lib provoca el error LNK2001 en `_beginthread`, `_beginthreadex`, `_endthread`, y `_endthreadex`.  
  
-   Vincular código que requiere las bibliotecas multiproceso \(cualquier código MFC o código compilado con [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)\) provoca el error LNK2001 en [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md), `_beginthreadex`, [\_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) y `_endthreadex`.  Vea el siguiente artículo de Knowledge Base para obtener más información:  
  
    -   Q126646 "PRB: Error Msg: LNK2001 on \_\_beginthreadex and \_\_endthreadex"  
  
    -   Q128641 "INFO: \/Mx Compiler Options and the LIBC, LIBCMT, MSVCRT Libs"  
  
    -   Q166504 "PRB: MFC and CRT Must Match in debug\/release and static\/dynamic"  
  
-   Al compilar con **\/MD**, una referencia a "func" en el código fuente se convierte en referencia "`__imp__func`" en el objeto, ya que todo el código en tiempo de ejecución se encuentra ahora en un archivo DLL.  Si se intenta vincular con las bibliotecas estáticas LIBC.lib o LIBCMT.lib, se obtiene el error LNK2001 en `__imp__func`.  Si se intenta vincular con MSVCxx.lib al compilar sin \/MD, no siempre se obtendrá LNK2001, pero probablemente habrá otros problemas.  
  
-   Vincular con las bibliotecas de modo de lanzamiento al compilar una versión de depuración de una aplicación puede causar LNK2001.  Del mismo modo, si se usa una opción **\/Mxd** \(**\/MTd** o **\/MDd**\) o se define `_DEBUG` y luego se vincula con las bibliotecas de modo de lanzamiento, es probable que se obtengan símbolos externos sin resolver \(entre otros problemas\).  Vincular una compilación de modo de lanzamiento con las bibliotecas de depuración también causará problemas similares.  
  
-   Mezclar versiones de las bibliotecas de Microsoft y productos de compiladores puede resultar problemático.  Las bibliotecas de una nueva versión del compilador pueden contener nuevos símbolos que no se encuentren en las bibliotecas incluidas en versiones anteriores.  Puede resultar conveniente cambiar el orden de los directorios en la ruta de búsqueda, o cambiarlos para que apunten a la versión actual.  
  
     El cuadro de diálogo Herramientas &#124; Opciones &#124; Proyectos &#124; Directorios de VC\+\+, en la selección de archivos de la biblioteca, permite cambiar el orden de búsqueda.  La carpeta Vinculador del cuadro de diálogo Páginas de propiedades del proyecto también puede contener rutas de acceso obsoletas.  
  
     Este problema puede aparecer al instalar un nuevo SDK \(quizás en una ubicación diferente\), y si el orden de búsqueda no se actualiza para que apunte a la nueva ubicación.  Normalmente, se debe colocar la ruta de acceso a los directorios de inclusión y de bibliotecas de los nuevos SDK delante de la ubicación predeterminada de Visual C\+\+.  Asimismo, un proyecto que contenga rutas de acceso incrustadas puede continuar señalando a rutas antiguas que son válidas pero obsoletas en lo que se refiere a las nuevas funciones que aporta la nueva versión, la cual se halla instalada en otra ubicación.  
  
-   Actualmente no hay un estándar para [denominación de C\+\+](../../error-messages/tool-errors/name-decoration.md) entre fabricantes de compiladores, ni entre versiones diferentes de un mismo compilador.  Por ello, vincular archivos objeto compilados con otros compiladores puede no producir el mismo esquema de denominación y causar por tanto el error LNK2001.  
  
-   [Mezclar opciones de compilación en línea y no en línea](../../error-messages/tool-errors/function-inlining-problems.md) en módulos diferentes puede causar el error LNK2001.  Si se crea una biblioteca de C\+\+ con la inclusión de funciones en línea activada \(**\/Ob1** u **\/Ob2**\) pero el archivo de encabezado correspondiente que describe las funciones la tiene desactivada \(no hay una palabra clave `inline`\), se obtiene este error.  Para evitar el problema, defina las funciones inline con `inline` en el archivo de encabezado que se incluirá en otros archivos.  
  
-   Si se utiliza la directiva de compilador `#pragma inline_depth`, hay que asegurarse de [establecer un valor de 2 o superior](../../error-messages/tool-errors/function-inlining-problems.md), y asegurarse también de que se está usando la opción del compilador [\/Ob1](../../build/reference/ob-inline-function-expansion.md) u [\/Ob2](../../build/reference/ob-inline-function-expansion.md).  
  
-   Omitir la opción de LINK \/NOENTRY al crear una DLL sólo de recursos causará el error LNK2001.  
  
-   Usar valores incorrectos de \/SUBSYSTEM o \/ENTRY puede generar el error LNK2001.  Por ejemplo, si crea una aplicación basada en caracteres \(una aplicación de consola\) y especifica \/SUBSYSTEM:WINDOWS, obtendrá un error de símbolo externo no resuelto para `WinMain`.  Para obtener más información sobre estas opciones y puntos de entrada, vea las opciones del vinculador [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) y [\/ENTRY](../../build/reference/entry-entry-point-symbol.md).  
  
 **Problemas de exportación**  
  
-   Al convertir una aplicación de 16 a 32 ó 64 bits, se puede generar el error LNK2001.  La sintaxis actual de archivo de definición de módulos \(.def\) requiere que se incluyan las funciones `__cdecl`, `__stdcall` y `__fastcall` en la sección EXPORTS sin subrayados \(sin decorar\).  Esto se diferencia de la sintaxis para 16 bits, donde deben ir con subrayados \(decoradas\).  Para obtener más información, vea la descripción de la sección [EXPORTS](../../build/reference/exports.md) de los archivos de definición de módulos.  
  
-   Cualquier exportación incluida en el archivo .def y no hallada causará el error LNK2001.  Ello puede deberse a que no existe, está escrito incorrectamente o usa nombres representativos de C\+\+ \(los archivos .def no toman nombres representativos\).  
  
 **Interpretar los resultados**  
  
 Cuando un símbolo está sin resolver, se puede obtener información sobre la función a partir de las siguientes directrices:  
  
 En plataformas x86, la convención de decoración de llamadas para los nombres compilados en C, o para los nombres extern "C" en C\+\+, es la siguiente:  
  
 `__cdecl`  
 La función tiene un prefijo de subrayado \(\_\).  
  
 `__stdcall`  
 La función tiene un prefijo de subrayado \(\_\) y un sufijo @ seguido del tamaño alineado con DWORD de los parámetros de la pila.  
  
 `__fastcall`  
 La función tiene un prefijo @ y un sufijo @ seguido del tamaño alineado con DWORD de los parámetros de la pila.  
  
 Use undname.exe para obtener la forma no decorada de un nombre representativo.  
  
 Para obtener más información sobre algunas de las causas expuestas anteriormente, vea [Creación de nombres representativos](../../error-messages/tool-errors/name-decoration.md).