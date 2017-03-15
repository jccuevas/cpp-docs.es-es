---
title: "C&#243;mo: Migrar a /clr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], trasladar"
  - "compilar código nativo [C++]"
  - "interoperabilidad [C++], /clr (opción del compilador)"
  - "interoperabilidad [C++], /clr (opción del compilador)"
  - "migración [C++], /clr (opción del compilador)"
  - "actualizar aplicaciones de Visual C++, /clr (opción del compilador)"
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# C&#243;mo: Migrar a /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describen los problemas que surgen al compilar el código nativo con **\/clr** \(vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información\).  **\/clr** permite invocar los módulos de Visual C\+\+ desde ensamblados .NET y viceversa, a la vez que mantiene la compatibilidad con módulos no administrados.  Vea [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md) e [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md) para obtener más información sobre las ventajas de compilar con **\/clr**.  
  
## Problemas conocidos al compilar proyectos de biblioteca con \/clr  
 Visual Studio contiene algunos problemas conocidos al compilar proyectos de biblioteca con **\/clr**:  
  
-   El código puede consultar los tipos en tiempo de ejecución con [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md).  Sin embargo, si un tipo está en un archivo .dll de MSIL \(compilado con **\/clr**\), la llamada a [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md) puede no completarse si se realiza antes de que los constructores estáticos se ejecuten en el archivo .dll administrado \(este problema no aparecerá si la llamada a FromName se produce una vez ejecutado el código en el archivo .dll administrado\).  Para solucionar este problema, puede forzar la creación del constructor estático administrado si define una función en el archivo .dll administrado, lo exporta y lo invoca desde la aplicación MFC nativa.  Por ejemplo:  
  
    ```  
    // Extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## Compilar con Visual C\+\+  
 Para poder usar **\/clr** en cualquier módulo del proyecto, primero compile y vincule el proyecto nativo con Visual Studio 2010.  
  
 Los pasos siguientes, realizados por orden, constituyen la forma más fácil de efectuar una compilación con **\/clr**.  Es importante compilar y ejecutar el proyecto después de cada uno de estos pasos.  
  
### Versiones anteriores a Visual C\+\+ 2003  
 Si se actualiza a Visual Studio 2010 desde una versión anterior a Visual C\+\+ 2003, puede que aparezcan errores de compilador relacionados con la conformidad con el estándar C\+\+ mejorado en Visual C\+\+ 2003.  
  
### Actualizar desde Visual C\+\+ 2003  
 Los proyectos compilados anteriormente con Visual C\+\+ 2003 también deben compilarse primero sin **\/clr**, ya que ahora se ha aumentado la conformidad con ANSI\/ISO y se han realizado algunos cambios importantes en Visual Studio.  El cambio que probablemente requiera más atención es [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).  Es muy probable que el código que utiliza CRT genere advertencias sobre elementos desusados.  Estas advertencias se pueden suprimir, pero es preferible migrar a las nuevas [Versiones de funciones de CRT con seguridad mejorada](../c-runtime-library/security-enhanced-versions-of-crt-functions.md), ya que proporcionan mayor seguridad y pueden revelar problemas de seguridad en el código.  
  
### Actualizar desde Extensiones administradas para C\+\+  
 Los proyectos compilados con Visual C\+\+ .NET o Visual C\+\+ 2003 que usaban Extensiones administradas para C\+\+ necesitarán al menos un cambio de configuración, ya que estas extensiones están desusadas.  Como resultado, el código escrito con Extensiones administradas para C\+\+ no se compilará bajo **\/clr**.  Utilice **\/clr:oldSyntax** en su lugar.  
  
## Convertir código de C en código de C\+\+  
 Aunque Visual Studio generará los archivos de C, es necesario convertirlos a C\+\+ para una compilación **\/clr**.  El nombre de archivo real no tiene que cambiarse; puede usar **\/Tp** \(vea [\/Tc, \/Tp, \/TC, \/TP \(Especificar el tipo de archivo de código fuente\)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)\). Tenga en cuenta que, aunque se requieren archivos de código fuente de C\+\+ para **\/clr**, no es necesario refactorizar el código para utilizar paradigmas orientados a objetos.  
  
 Es muy probable que el código de C requiera cambios cuando se compile como un archivo de C\+\+.  Las reglas de seguridad de tipos de C\+\+ son estrictas, por lo que las conversiones de tipos se deben realizar de forma explícita.  Por ejemplo, malloc devuelve un puntero nulo, pero se puede asignar a un puntero de cualquier tipo de C con una conversión:  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 Los punteros a función también presentan una seguridad de tipos estricta en C\+\+, por lo que el siguiente código de C requiere alguna modificación.  En C\+\+, es mejor crear un especificador `typedef` que defina el tipo de puntero a función y, a continuación, utilizar dicho tipo para convertir los punteros de función:  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C\+\+ también requiere que se creen prototipos de las funciones o se definan totalmente para que se pueda hacer referencia a ellas o se puedan invocar.  
  
 Se debe cambiar el nombre de los identificadores utilizados en el código de C que resulten ser palabras clave en C\+\+ \(como `virtual`, `new`, `delete`, `bool`, `true`, `false`, etc.\).  Esto generalmente se puede hacer con operaciones simples de búsqueda y sustitución.  
  
 Finalmente, mientras que las llamadas COM de estilo C requieren el uso explícito de v\-table y del puntero `this`, C\+\+ no lo requiere:  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## Redefinir la configuración del proyecto  
 Después de que su proyecto se compile y se ejecute en Visual Studio 2010, debe crear nuevas configuraciones del proyecto para **\/clr** en lugar de modificar las configuraciones predeterminadas.  **\/clr** es incompatible con algunas opciones del compilador, pero la creación de configuraciones independientes le permite compilar el proyecto como nativo o administrado.  Si se selecciona **\/clr** en el cuadro de diálogo Páginas de propiedades, los parámetros de configuración del proyecto que no sean compatibles con **\/clr** se deshabilitan \(y las opciones deshabilitadas no se restauran automáticamente si **\/clr** se desactiva posteriormente\).  
  
### Crear nuevas configuraciones de proyecto  
 Puede utilizar la opción **Copiar configuración de** en el [New Project Configuration Dialog Box](http://msdn.microsoft.com/es-es/cca616dc-05a6-4fe3-bdc1-40c72a66f2be) para crear una configuración de proyecto basada en los parámetros del proyecto existentes.  Haga esto una vez para la configuración de depuración y una vez para la configuración Release.  Los cambios posteriores se podrán aplicar después a las configuraciones específicas de **\/clr**, lo que deja intactas las configuraciones de proyecto originales.  
  
 Los proyectos que usan reglas de compilación personalizadas pueden requerir más atención.  
  
 Este paso tiene implicaciones diferentes para los proyectos que utilizan archivos Make.  En este caso, se puede configurar un destino de compilación independiente o se puede crear una compilación específica de la versión de **\/clr** a partir de una copia del original.  
  
### Cambiar la configuración del proyecto  
 **\/clr** se puede seleccionar en el entorno de desarrollo siguiendo las instrucciones de [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  Como se mencionó previamente, este paso deshabilitará automáticamente los parámetros de configuración del proyecto en conflicto.  
  
> [!NOTE]
>  Si se actualiza un proyecto de biblioteca administrada o de servicio Web desde Visual C\+\+ 2003, la opción del compilador **\/Zl** se agregará a la página de propiedades **Línea de comandos**.  Esto produce el error LNK2001.  Quite **\/Zl** de la página de propiedades **Línea de comandos** para resolverlo.  Para obtener más información, vea [\/Zl \(Omitir nombres de biblioteca predeterminada\)](../build/reference/zl-omit-default-library-name.md) y [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  O bien, agregue msvcrt.lib y msvcmrt.lib a la propiedad **Dependencias adicionales** del vinculador.  
  
 Para los proyectos generados con archivos Make, las opciones del compilador incompatibles se deben deshabilitar manualmente una vez agregado **\/clr**.  Vea [Restricciones de \/clr](../build/reference/clr-restrictions.md) para obtener información sobre las opciones del compilador que no son compatibles con **\/clr**.  
  
### Encabezados precompilados  
 **\/clr** admite los encabezados precompilados.  No obstante, si solo compila algunos de los archivos CPP con **\/clr** \(y compila el resto como archivos nativos\), deberá realizar algunos cambios ya que los encabezados precompilados generados con **\/clr** no son compatibles con los generados sin **\/clr**.  Esta incompatibilidad se debe al hecho de que **\/clr** genera y requiere metadatos.  Por lo tanto, los módulos compilados con **\/clr** no pueden usar encabezados precompilados que no incluyan metadatos y los módulos no compilados con **\/clr** no pueden usar archivos de encabezado precompilados que contengan metadatos.  
  
 La manera más fácil de compilar un proyecto en el que algunos módulos se compilan con **\/clr** consiste en deshabilitar completamente los encabezados precompilados. \(En el cuadro de diálogo Páginas de propiedades del proyecto, abra el nodo C\/C\+\+ y seleccione Encabezados precompilados.  A continuación, cambie la propiedad Crear\/Utilizar encabezado precompilado a "No utilizar encabezados precompilados"\).  
  
 Sin embargo, particularmente para los proyectos grandes, los encabezados precompilados proporcionan una velocidad de compilación mucho mayor, de modo que no es deseable deshabilitar esta característica.  En este caso, es mejor configurar los archivos **\/clr** y no **\/clr** para utilizar encabezados precompilados independientes.  Esto se puede realizar en un solo paso mediante la selección múltiple de los módulos que se van a compilar con **\/clr**; para ello, utilice el Explorador de soluciones, haga clic con el botón secundario en el grupo y seleccione Propiedades.  A continuación, cambie las propiedades Crear o utilizar encabezado precompilado a través de archivo y Archivo de encabezado precompilado para utilizar un nombre de archivo de encabezado y un archivo PCH diferentes, respectivamente.  
  
## Corregir errores  
 Compilar con **\/clr** puede producir errores de compilador, del vinculador o del runtime.  En esta sección se describen los problemas más comunes.  
  
### Combinación de metadatos  
 Las distintas versiones de los tipos de datos pueden hacer que el vinculador produzca un error debido a que los metadatos generados para los dos tipos no coinciden. \(Esto ocurre normalmente cuando los miembros de un tipo se definen condicionalmente, pero las condiciones no son las mismas para todos los archivos CPP que usan dicho tipo\). En este caso, el vinculador produce un error y solo notifica el nombre de símbolo y el nombre del segundo archivo OBJ en el que se definió el tipo.  A menudo resulta útil invertir el orden en que se envían los archivos OBJ al vinculador para detectar la ubicación de la otra versión del tipo de datos.  
  
### Interbloqueo de bloqueo del cargador  
 En Visual C\+\+ .NET y Visual C\+\+ 2003, la inicialización bajo **\/clr** era susceptible al interbloqueo no determinista.  Este problema se conoce como "interbloqueo de bloqueo del cargador".  En Visual Studio 2010, este interbloqueo es más fácil de evitar, se detecta y se notifica en el runtime y ya no es no determinista.  Encontrar el problema de bloqueo del cargador todavía es posible, pero ahora es mucho más fácil de evitar y corregir.  Vea [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md) para obtener información detallada, orientación y soluciones.  
  
### Exportaciones de datos  
 La exportación de datos DLL es propensa a errores y no se recomienda.  Esto se debe a que no se garantiza que se inicialice la sección de datos de una DLL hasta que se haya ejecutado alguna parte administrada de la DLL.  Haga referencia a los metadatos con [\#using \(Directiva\)](../preprocessor/hash-using-directive-cpp.md).  
  
### Visibilidad de tipos  
 Los tipos nativos ahora son privados de forma predeterminada.  En Visual C\+\+ .NET 2002 y Visual C\+\+ 2003, los tipos nativos eran públicos de forma predeterminada.  Esto puede producir un tipo nativo que no sea visible fuera de la DLL.  Para resolver este error, agregue `public` a estos tipos.  Para obtener más información, vea [Visibilidad de tipos y de miembros](../misc/type-and-member-visibility.md).  
  
### Problemas de punto flotante y alineación  
 `__controlfp` no se admite en Common Language Runtime \(vea [\_control87, \_controlfp, \_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener más información\).  CLR tampoco respetará [align](../cpp/align-cpp.md).  
  
### Inicialización COM  
 Common Language Runtime inicializa COM automáticamente cuando se inicializa un módulo \(cuando se inicializa COM automáticamente, se hace en forma de MTA\).  Como resultado, la inicialización explícita de COM produce códigos devueltos que indican que COM ya se ha inicializado.  El intento de inicializar COM explícitamente con un modelo de subprocesos cuando CLR ya ha inicializado COM en otro modelo de subprocesos puede hacer que la aplicación no funcione correctamente.  
  
 Common Language Runtime inicia COM de forma predeterminada como MTA; utilice [\/CLRTHREADATTRIBUTE \(Establecer el atributo de subproceso de CLR\)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) para modificar este comportamiento.  
  
### Problemas de rendimiento  
 Puede que disminuya el rendimiento si los métodos de C\+\+ nativos generados para MSIL se llaman indirectamente \(llamadas a funciones virtuales o uso de punteros de función\).  Para obtener más información sobre esto, vea [Doble thunk](../dotnet/double-thunking-cpp.md).  
  
 Al pasar de código nativo a código MSIL, observará un aumento en el tamaño del espacio de trabajo.  Esto se debe a que Common Language Runtime proporciona muchas características para garantizar que los programas se ejecuten correctamente.  Si la aplicación **\/clr** no se ejecuta correctamente, puede habilitar C4793 \(desactivado de forma predeterminada\); vea [Advertencia del compilador \(niveles 1 y 3\) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md) para obtener más información.  
  
### El programa se bloquea o se cierra  
 En algunos casos, CLR puede cerrarse antes de que el código administrado termine de ejecutarse.  El uso de `std::set_terminate` y `SIGTERM` puede producir esto.  Para obtener más información, vea [signal \(Constantes\)](../c-runtime-library/signal-constants.md) y [set\_terminate](../Topic/set_terminate%20\(%3Cexception%3E\).md).  
  
## Utilizar las nuevas características de Visual C\+\+  
 Una vez compilada, vinculada y ejecutada la aplicación, puede empezar a utilizar las características de .NET en cualquier módulo compilado con **\/clr**.  Para obtener más información, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).  
  
 Si utilizó las Extensiones administradas para C\+\+, puede convertir el código para usar la nueva sintaxis.  Para obtener un resumen de las diferencias sintácticas, vea la [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/es-es/edbded88-7ef3-4757-bd9d-b8f48ac2aada).  Para obtener detalles sobre cómo convertir las Extensiones administradas para C\+\+, vea [Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md).  
  
 Para obtener información sobre la programación de .NET en Visual C\+\+, vea:  
  
-   [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)