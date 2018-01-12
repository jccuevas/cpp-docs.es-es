---
title: "Cómo: migrar a - clr: pure (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], migrating to /clr:pure
- migration [C++], pure MSIL
- pure MSIL [C++], porting to
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b8d49ee233167c02570408ba091c2a99b78487d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-migrate-to-clrpure-ccli"></a>Cómo: Migrar a /clr:pure (C++/CLI)
En este tema se aborda los problemas que pueden surgir al migrar a MSIL puro utilizando **/CLR: pure** (consulte [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información). En este tema se da por supuesto que el código que se está migrando está compilado como ensamblado mixto mediante la **/CLR** opción, como la ruta de acceso de migración desde código no administrado a MSIL puro no es directa. Para código no administrado, consulte [Cómo: migrar a/CLR](../dotnet/how-to-migrate-to-clr.md) antes de intentar migrar a MSIL puro.  
  
## <a name="basic-changes"></a>Cambios básicos  
 MSIL puro consta de instrucciones MSIL, por lo que el código que contiene funciones que no se pueden expresar en MSIL impide la compilación. Esto incluye las funciones definidas como mediante convenciones de llamada distinto de [__clrcall](../cpp/clrcall.md). (Funciones __clrcall no pueden se invoca en un componente MSIL puro, pero no definidas).  
  
 Para asegurarse de que no hay errores en tiempo de ejecución, debe habilitar la advertencia C4412. Habilitar C4412 agregando `#pragma warning (default : 4412)` para cada operación de compilación que se compilan con **/CLR: pure** y que pase tipos de C++ desde y hacia IJW (**/CLR)** o código nativo. Vea [advertencia del compilador (nivel 2) C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) para obtener más información.  
  
## <a name="architectural-considerations"></a>Consideraciones sobre la arquitectura  
 Algunas de las limitaciones de los ensamblados MSIL puros indicadas en [código puro y comprobable (C++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) tiene implicaciones de alto nivel de la estrategia de migración y diseño de la aplicación. En concreto, a diferencia de los ensamblados mixtos, los ensamblados MSIL puros no tienen compatibilidad completa con módulos no administrados.  
  
 Los ensamblados MSIL puros pueden llamar a funciones no administradas, pero no se puede llamar a funciones no administradas. Como resultado, MSIL puro es mejor candidato para el código de cliente que usa funciones no administradas que hacerlo para el código de servidor que se usa por funciones no administradas. Si la funcionalidad contenida en un ensamblado MSIL puro va a ser utilizado por funciones no administradas, debe utilizarse un ensamblado mixto como capa de interfaz.  
  
 Las aplicaciones que utilizan ATL o MFC no son buenos candidatos para la migración a MSIL puro, como estas bibliotecas no se admiten en esta versión. Del mismo modo, el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] contiene archivos de encabezado que no se compilan en **/CLR: pure**.  
  
 Mientras los ensamblados MSIL puros pueden llamar a funciones no administradas, esta capacidad se limita a las funciones de estilo C simples. El uso de API no administradas más complejas es probable que se requiera la funcionalidad no administrada que se expondrán en forma de una interfaz COM o un ensamblado mixto que pueda actuar como una interfaz entre el MSIL puro y componentes no administrados. Uso de una capa de ensamblado mixto es la única forma de utilizar funciones no administradas que tomen funciones de devolución de llamada, por ejemplo, cuando un ensamblado puro no puede proporcionar una función nativa que se puede llamar para su uso como una devolución de llamada.  
  
## <a name="application-domains-and-calling-conventions"></a>Dominios de aplicación y convenciones de llamada  
 Aunque es posible en el MSIL puro ensamblados utilizan funciones no administradas, funciones y datos estáticos se tratan de forma diferente. En los ensamblados puros, las funciones se implementan con la [__clrcall](../cpp/clrcall.md) convención de llamada y datos estáticos es almacenado por dominio de aplicación. Esto difiere del valor predeterminado para los ensamblados mixtos y no administrados que utiliza el [__cdecl](../cpp/cdecl.md) convención de llamada de funciones y almacenar datos estáticos en una base por proceso.  
  
 En el contexto de MSIL puro (y código comprobable compilado con/CLR: safe), estos valores predeterminados son transparentes, como [__clrcall](../cpp/clrcall.md) es la convención llamada predeterminada de CLR y dominios de aplicación son el ámbito nativo para estático y datos globales en aplicaciones. NET. Sin embargo, cuando se interactúa con componentes que no administrados o mixtos, el tratamiento de datos globales y funciones diferente puede causar problemas.  
  
 Por ejemplo, si un componente MSIL puro es llamar a funciones en un archivo DLL no administrado o mixto, se utilizará un archivo de encabezado para el archivo DLL para compilar el ensamblado puro. Sin embargo, a menos que la convención de llamada para cada función en el encabezado se indica explícitamente, supondrá que [__clrcall](../cpp/clrcall.md). Esto producirá posteriormente errores en tiempo de ejecución, como estas funciones suelen implementar con el [__cdecl](../cpp/cdecl.md) convención. Las funciones en el archivo de encabezado no administrado se pueden marcar explícitamente como [__cdecl](../cpp/cdecl.md), o se debe volver a compilar todo el código de origen de archivo DLL en **/CLR: pure**.  
  
 Del mismo modo, se supone que los punteros de función para que apunte a [__clrcall](../cpp/clrcall.md) funciona en **/CLR: pure** compilación. Estos demasiado deben agregar explícitamente con la convención de llamada correcta.  
  
 Para obtener más información, consulte [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="linking-limitations"></a>Limitaciones de la vinculación  
 El vinculador de Visual C++ no intentará vincular archivos OBJ mixtos y puros, ya que las convenciones de ámbito y llamar al método de almacenamiento son diferentes.  
  
## <a name="see-also"></a>Vea también  
 [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)