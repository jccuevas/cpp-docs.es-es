---
title: "C&#243;digo puro y comprobable (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], código puro y comprobable"
  - "/clr (opción del compilador) [C++], ensamblados mixtos"
  - "/clr (opción del compilador) [C++], ensamblados puros"
  - "/clr (opción del compilador) [C++], ensamblados comprobables"
  - "ensamblados [C++], código mixto"
  - "ensamblados [C++], código puro"
  - "ensamblados [C++], código comprobable"
  - "ensamblados mixtos [C++]"
  - "ensamblados mixtos [C++], acerca de los ensamblados mixtos"
  - "MSIL puro [C++]"
  - "MSIL puro [C++], acerca del código puro"
  - "ensamblados comprobables [C++]"
  - "ensamblados comprobables [C++], acerca de los ensamblados comprobables"
  - "código seguro comprobable [C++]"
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;digo puro y comprobable (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para la programación .NET, Visual C\+\+ admite la creación de tres tipos distintos de componentes y aplicaciones: mixto, puro y comprobable.  Los tres están disponibles a través de la opción del compilador [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## Comentarios  
 Para obtener más información acerca de los ensamblados comprobables, vea:  
  
-   [Comparación de características mixta, pura y comprobable](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [Cómo: Migrar a \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [Cómo: Crear proyectos de C\+\+ comprobables](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [Cómo: Migrar a \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [Utilizar ensamblados comprobables con SQL Server](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [Procedimientos recomendados](../top/security-best-practices-for-cpp.md)  
  
-   [Convertir proyectos de modo mixto a lenguaje intermedio puro](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## Mixta \(\/clr\)  
 Los ensamblados mixtos \(compilados con **\/clr**\), contienen partes administradas y no administradas, lo que les permite utilizar las características .NET, pero siguen conteniendo código no administrado.  Esto permite actualizar aplicaciones y componentes para utilizar las características de .NET sin tener que volver a escribir el proyecto completo.  El uso de Visual C\+\+ para mezclar código administrado y no administrado de este modo se denomina interoperabilidad de C\+\+.  Para obtener más información, vea [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md) y [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md).  
  
## Pura \(\/clr:pure\)  
 Los ensamblados puros \(compilados con **\/clr:pure**\) pueden contener tipos de datos administrados y nativos, pero solo funciones administradas.  Al igual que los ensamblados mixtos, los ensamblados puros permiten la interoperabilidad con archivos DLL nativos a través de P\/Invoke \(vea [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)\), pero las características de interoperabilidad de C\+\+ no están disponibles.  Además, los ensamblados puros no pueden exportar funciones que son invocables desde funciones nativas, porque los puntos de entrada de un ensamblado puro utilizan la convención de llamada [\_\_clrcall](../cpp/clrcall.md).  
  
### Ventajas de \/clr:pure  
  
-   Mejor rendimiento: dado que los ensamblados puros solo contienen MSIL, no hay ninguna función nativa y, por consiguiente, no es necesaria ninguna transición entre función administrada y no administrada. \(Las llamadas a funciones realizadas a través de P\/Invoke son una excepción a esta regla\).  
  
-   Conocimiento de AppDomain: las funciones administradas y los tipos de datos de CLR existen dentro de los `Application Domains`, lo que afecta a su visibilidad y accesibilidad.  Los ensamblados puros tienen en cuenta el dominio \(\_\_declspec \([appdomain](../cpp/appdomain.md)\) se supone para cada tipo\), por lo que el acceso a sus tipos y funcionalidad desde otros componentes de .NET es más fácil y más seguro.  Como resultado, los ensamblados puros interoperan más fácilmente con otros componentes de .NET que los ensamblados mixtos.  
  
-   No se cargan en disco: los ensamblados puros se pueden cargar en memoria e incluso transmitirse en secuencias.  Esto es esencial para utilizar los ensamblados .NET como procedimientos almacenados.  Esto es diferente en los ensamblados mixtos, los cuales deben estar en el disco para ejecutarse, debido a una dependencia de los mecanismos de carga de Windows.  
  
-   Reflexión: no es posible reflejar en archivos ejecutables mixtos, mientras que los ensamblados puros admiten por completo la reflexión.  Para obtener más información, vea [Reflexión](../dotnet/reflection-cpp-cli.md).  
  
-   Capacidad de control del host: dado que los ensamblados puros solo contienen MSIL, se comportan de forma más predecible y flexible que los ensamblados mixtos cuando se utilizan en aplicaciones que hospeden CLR y modifiquen su comportamiento predeterminado.  
  
### Limitaciones de \/clr:pure  
 Esta sección trata sobre características no admitidas actualmente por **\/clr:pure**.  
  
-   Las funciones no administradas no pueden llamar a ensamblados puros.  Por consiguiente, los ensamblados puros no pueden implementar interfaces COM ni exponer devoluciones de llamada nativas.  Los ensamblados puros no pueden exportar funciones a través de archivos \_\_declspec\(dllexport\) o .DEF.  Asimismo, las funciones declaradas con la convención \_\_clrcall no se pueden importar a través de \_\_declspec\(dllimport\).  Las funciones de un módulo nativo se pueden llamar desde ensamblados puros, pero estos no pueden exponer funciones nativas invocables, de modo que la funcionalidad de un ensamblado puro se debe exponer a través de funciones administradas en un ensamblado mixto.  Vea [Cómo: Migrar a \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) para obtener más información.  
  
-   La compilación en modo puro de Visual C\+\+ no admite las bibliotecas ATL y MFC.  
  
-   Los archivos .netmodules puros no se aceptan como entrada del vinculador de Visual C\+\+.  Sin embargo, el vinculador acepta archivos .obj puros, que contienen un supraconjunto de la información incluida en los archivos .netmodules.  Para obtener más información, vea [.Archivos netmodule como entrada del vinculador](../build/reference/netmodule-files-as-linker-input.md).  
  
-   No se admite la compatibilidad con COM del compilador \(\#import\), ya que esto introduciría instrucciones no administradas en el ensamblado puro.  
  
-   Las opciones de punto flotante para la alineación y el control de excepciones no son ajustables para los ensamblados puros.  En consecuencia, no se puede utilizar \_\_declspec\(align\).  Esto hace que algunos archivos de encabezado, como fpieee.h, no sean compatibles con \/clr:pure.  
  
-   La función GetLastError de PSDK puede presentar un comportamiento indefinido si se compila con **\/clr:pure**.  
  
## Comprobable \(\/clr:safe\)  
 La opción del compilador **\/clr:safe** genera ensamblados comprobables, como los escritos en Visual Basic y C\#, que cumplen los requisitos que permiten a Common Language Runtime \(CLR\) garantizar que el código no infringe la configuración de seguridad actual.  Por ejemplo, si la configuración de seguridad prohíbe a un componente escribir en disco, CLR puede determinar si el componente comprobable cumple este criterio antes de ejecutar el código.  CRT no ofrece compatibilidad con los ensamblados comprobables. \(La compatibilidad de CRT con los ensamblados puros se logra a través de una versión pura de MSIL de la biblioteca en tiempo de ejecución de C\).  
  
 Los ensamblados comprobables proporcionan estas ventajas sobre los ensamblados puros y mixtos:  
  
-   Mayor seguridad.  
  
-   Algunas situaciones la requieren \(por ejemplo, el uso de componentes SQL\).  
  
-   Las versiones futuras de Windows exigirán cada vez más que los componentes y las aplicaciones sean comprobables.  
  
 Una desventaja consisten en que las características de interoperabilidad de C\+\+ no están disponibles.  Los ensamblados comprobables no pueden contener ninguna función no administrada ni tipos de datos nativos, aunque el código administrado no haga referencia a ellos.  
  
 A pesar del uso de la palabra "safe", la compilación de aplicaciones con **\/clr:safe** no significa que no haya errores; solo significa que CLR puede comprobar la configuración de seguridad en tiempo de ejecución.  
  
 Independientemente del tipo de ensamblado, las llamadas realizadas desde ensamblados administrados a archivos DLL nativos a través de P\/Invoke se compilarán, pero puede que produzcan errores en tiempo de ejecución según la configuración de seguridad que se use.  
  
> [!NOTE]
>  Existe un escenario de codificación que cumplirá los requisitos del compilador, pero que dará como resultado un ensamblado no comprobable: llamar a una función virtual a través de una instancia de objeto mediante un operador de resolución de ámbito.  Por ejemplo: `MyObj -> A::VirtualFunction();`.  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)