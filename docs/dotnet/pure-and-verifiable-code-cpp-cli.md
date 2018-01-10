---
title: "Código puro y comprobable (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7bcaabb9f0a696a5eb7b01c4bd78757681e4e6a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pure-and-verifiable-code-ccli"></a>Código puro y comprobable (C++/CLI)
Para la programación .NET, Visual C++ admite la creación de tres tipos distintos de componentes y aplicaciones: mixto, puro y comprobable. Las tres están disponibles a través de la [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los ensamblados comprobables, vea:  
  
-   [Comparación de características mixta, pura y comprobable (C++/CLI)](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [Cómo: migrar a/CLR: pure (C++ / CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [Cómo: Crear proyectos de C++ comprobables (C++/CLI)](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [Cómo: migrar a/CLR: safe (C++ / CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [Usar ensamblados comprobables con SQL Server (C++/CLI)](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [Procedimientos recomendados para la seguridad](../security/security-best-practices-for-cpp.md)  
  
-   [Convertir proyectos de modo mixto a lenguaje intermedio puro](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## <a name="mixed-clr"></a>Mixta (/clr)  
 Ensamblados mixtos (compilados con **/CLR**), contienen no administrado y partes administradas, lo que les permite utilizar características. NET, pero siguen contengan código no administrado. Esto permite actualizar aplicaciones y componentes para utilizar las características de .NET sin tener que volver a escribir el proyecto completo. El uso de Visual C++ para mezclar código administrado y no administrado de este modo se denomina interoperabilidad de C++. Para obtener más información, consulte [ensamblados mixto (nativo y administrado)](../dotnet/mixed-native-and-managed-assemblies.md) y [nativo y la interoperabilidad de .NET](../dotnet/native-and-dotnet-interoperability.md).  
  
## <a name="pure-clrpure"></a>Pura (/clr:pure)  
 Los ensamblados puros (compilados con **/CLR: pure**) puede contener dos tipos de datos nativos y administrados, pero solo funciones administradas. Al igual que los ensamblados mixtos, los ensamblados puros permiten la interoperabilidad con archivos DLL nativos a través de P/Invoke (vea [Using PInvoke explícito en C++ (atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)), pero las características de interoperabilidad de C++ no están disponibles. Además, los ensamblados puros no pueden exportar funciones que se pueda llamadas desde funciones nativas porque los puntos de entrada en un ensamblado puro, use la [__clrcall](../cpp/clrcall.md) convención de llamada.  
  
### <a name="advantages-of-clrpure"></a>Ventajas de /clr:pure  
  
-   Mejor rendimiento: dado que los ensamblados puros solo contienen MSIL, no hay ninguna función nativa y, por consiguiente, no es necesaria ninguna transición entre función administrada y no administrada. (Las llamadas a funciones realizadas a través de P/Invoke son una excepción a esta regla).  
  
-   Conocimiento de AppDomain: las funciones administradas y los tipos de datos de CLR existen dentro de los `Application Domains`, lo que afecta a su visibilidad y accesibilidad. Los ensamblados puros son conscientes del dominio (__declspec ([appdomain](../cpp/appdomain.md)) está implícito para cada tipo) para tener acceso a sus tipos y la funcionalidad de otros componentes de .NET es más fácil y más segura. Como resultado, los ensamblados puros interoperan más fácilmente con otros componentes de .NET que los ensamblados mixtos.  
  
-   No se cargan en disco: los ensamblados puros se pueden cargar en memoria e incluso transmitirse en secuencias. Esto es esencial para utilizar los ensamblados .NET como procedimientos almacenados. Esto es diferente en los ensamblados mixtos, los cuales deben estar en el disco para ejecutarse, debido a una dependencia de los mecanismos de carga de Windows.  
  
-   Reflexión: no es posible reflejar en archivos ejecutables mixtos, mientras que los ensamblados puros admiten por completo la reflexión. Para obtener más información, consulte [reflexión (C++ / CLI)](../dotnet/reflection-cpp-cli.md).  
  
-   Capacidad de control del host: dado que los ensamblados puros solo contienen MSIL, se comportan de forma más predecible y flexible que los ensamblados mixtos cuando se utilizan en aplicaciones que hospeden CLR y modifiquen su comportamiento predeterminado.  
  
### <a name="limitations-of-clrpure"></a>Limitaciones de /clr:pure  
 Esta sección trata sobre características no admitidas actualmente por **/CLR: pure**.  
  
-   Las funciones no administradas no pueden llamar a ensamblados puros. Por consiguiente, los ensamblados puros no pueden implementar interfaces COM ni exponer devoluciones de llamada nativas. Los ensamblados puros no pueden exportar funciones a través de archivos __declspec(dllexport) o .DEF. Además, las funciones declaradas con el \__clrcall convención no se puede importar a través de \__declspec (dllimport). Las funciones de un módulo nativo se pueden llamar desde ensamblados puros, pero estos no pueden exponer funciones nativas invocables, de modo que la funcionalidad de un ensamblado puro se debe exponer a través de funciones administradas en un ensamblado mixto. Vea [Cómo: migrar a/CLR: pure (C++ / CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) para obtener más información.  
  
-   La compilación en modo puro de Visual C++ no admite las bibliotecas ATL y MFC.  
  
-   Los archivos .netmodules puros no se aceptan como entrada del vinculador de Visual C++. Sin embargo, el vinculador acepta archivos .obj puros, que contienen un supraconjunto de la información incluida en los archivos .netmodules. Vea [archivos .netmodule como entrada del vinculador](../build/reference/netmodule-files-as-linker-input.md) para obtener más información.  
  
-   No se admite la compatibilidad con COM del compilador (#import), ya que esto introduciría instrucciones no administradas en el ensamblado puro.  
  
-   Las opciones de punto flotante para la alineación y el control de excepciones no son ajustables para los ensamblados puros. En consecuencia, no se puede utilizar __declspec(align). Esto hace que algunos archivos de encabezado, como fpieee.h, no sean compatibles con /clr:pure.  
  
-   La función GetLastError de PSDK puede presentar un comportamiento indefinido si se compila con **/CLR: pure**.  
  
## <a name="verifiable-clrsafe"></a>Comprobable (/clr:safe)  
 El **/CLR: safe** opción del compilador genera ensamblados comprobables, como los escritos en Visual Basic y C#, que cumplen los requisitos que permiten a common language runtime (CLR) para garantizar que el código no infringe actual configuración de seguridad. Por ejemplo, si la configuración de seguridad prohíbe a un componente escribir en disco, CLR puede determinar si el componente comprobable cumple este criterio antes de ejecutar el código. CRT no ofrece compatibilidad con los ensamblados comprobables. (La compatibilidad de CRT con los ensamblados puros se logra a través de una versión pura de MSIL de la biblioteca en tiempo de ejecución de C).  
  
 Los ensamblados comprobables proporcionan estas ventajas sobre los ensamblados puros y mixtos:  
  
-   Mayor seguridad.  
  
-   Algunas situaciones la requieren (por ejemplo, el uso de componentes SQL).  
  
-   Las versiones futuras de Windows exigirán cada vez más que los componentes y las aplicaciones sean comprobables.  
  
 Una desventaja consisten en que las características de interoperabilidad de C++ no están disponibles. Los ensamblados comprobables no pueden contener ninguna función no administrada ni tipos de datos nativos, aunque el código administrado no haga referencia a ellos.  
  
 A pesar del uso de la palabra "safe", la compilación de aplicaciones con **/CLR: safe** no significa que haya errores; simplemente significa que el CLR puede comprobar la configuración de seguridad en tiempo de ejecución.  
  
 Independientemente del tipo de ensamblado, las llamadas realizadas desde ensamblados administrados a archivos DLL nativos a través de P/Invoke se compilarán, pero puede que produzcan errores en tiempo de ejecución según la configuración de seguridad que se use.  
  
> [!NOTE]
>  Existe un escenario de codificación que cumplirá los requisitos del compilador, pero que dará como resultado un ensamblado no comprobable: llamar a una función virtual a través de una instancia de objeto mediante un operador de resolución de ámbito.  Por ejemplo: `MyObj -> A::VirtualFunction();`.  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)