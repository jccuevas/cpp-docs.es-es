---
title: Mixto (nativos y administrados) ensamblados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0ac18841d5050bc8fb849ac542dc298ce89c964f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mixed-native-and-managed-assemblies"></a>Ensamblados mixtos (nativos y administrados)
Los ensamblados mixtos son capaces de contener tanto instrucciones máquina no administradas como instrucciones MSIL. Esto les permite llamar y ser llamados por componentes .NET, a la vez que conservan la compatibilidad con componentes totalmente no administrados. Mediante ensamblados mixtos, los desarrolladores pueden crear aplicaciones con una combinación de funcionalidad administrada y no administrada. Esto crea ensamblados mixtos ideales para migrar aplicaciones existentes de Visual C++ a la plataforma .NET.  
  
 Por ejemplo, una aplicación existente que se compone únicamente de funciones no administradas se puede poner a la plataforma .NET volviendo a compilar sólo un módulo con el **/CLR** modificador del compilador. Este módulo puede utilizar las características de .NET pero sigue siendo compatible con el resto de la aplicación. De esta manera, una aplicación se puede convertir a la plataforma .NET de un modo gradual, por partes. Incluso es posible decidir entre compilación administrada y según una función por función dentro del mismo archivo (vea [managed, unmanaged](../preprocessor/managed-unmanaged.md)).  
  
 Visual C++ admite la generación de tres tipos distintos de ensamblados administrados: mixto, puro y comprobable. Los dos últimos se explican en [código puro y comprobable (C++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: migrar a/CLR](../dotnet/how-to-migrate-to-clr.md)  
 Describe los pasos recomendados para introducir o actualizar la funcionalidad de .NET en la aplicación.  
  
 [Cómo: compilar MFC y ATL código mediante /clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 Explica cómo compilar los programas MFC y ATL existentes para usarlos en Common Language Runtime.  
  
 [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)  
 Describe el problema del "bloqueo del cargador" y soluciones.  
  
 [Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)  
 Explica cómo utilizar bibliotecas nativas en **/CLR** compilaciones.  
  
 [Consideraciones sobre el rendimiento](../dotnet/performance-considerations-for-interop-cpp.md)  
 Describe las implicaciones de rendimiento de los ensamblados mixtos y la serialización de datos.  
  
 [Dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md)  
 Explica la compatibilidad de Visual C++ para dominios de aplicación.  
  
 [Doble thunk](../dotnet/double-thunking-cpp.md)  
 Trata de las implicaciones de rendimiento de un punto de entrada nativo para una función administrada.  
  
 [Evitar excepciones CLR apagado cuando se utilizan objetos COM compilados con/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 Explica cómo garantizar un apagado correcto de una aplicación administrada que utiliza un objeto COM compilado con **/CLR**.  
  
 [Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT](../dotnet/create-a-partially-trusted-application.md)  
 Describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++, quitando la dependencia de msvcm90.dll.  
  
 Para obtener más información sobre cómo codificar instrucciones para ensamblados mixtos, vea el artículo MSDN "An Overview of Managed/Unmanaged Code Interoperability" en [ http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp ](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp).  
  
## <a name="see-also"></a>Vea también  
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)