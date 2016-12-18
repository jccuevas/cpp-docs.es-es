---
title: "C&#243;mo: Migrar a /clr:pure (C++/CLI) | Microsoft Docs"
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
  - "/clr (opción del compilador) [C++], migrar a /clr:pure"
  - "migración [C++], MSIL puro"
  - "MSIL puro [C++], trasladar"
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Migrar a /clr:pure (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema trata de problemas que pueden surgir al migrar a MSIL puro utilizando **\/clr:pure** \(vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información\).  En el tema, se supone que el código que se migra está compilado como ensamblado mixto mediante la opción **\/clr**, ya que la ruta de migración de código no administrado a MSIL puro no es directa.  Para código no administrado, vea [Cómo: Migrar a \/clr](../dotnet/how-to-migrate-to-clr.md) antes de tratar de migrar a MSIL puro.  
  
## Cambios básicos  
 Un componente MSIL puro está compuesto por instrucciones MSIL, por lo que el código que contiene funciones que no se pueden expresar en MSIL impide la compilación.  Esto incluye funciones que se definen por usar convenciones de llamada distintas de [\_\_clrcall](../cpp/clrcall.md). \(Las funciones distintas de \_\_clrcall se pueden invocar en un componente MSIL puro, pero no definir.\)  
  
 Para garantizar que no hay errores en tiempo de ejecución, se debe habilitar la advertencia C4412.  Para hacerlo, agregue `#pragma warning (default : 4412)` a cada operación de compilación que efectúe con **\/clr:pure** y que pase tipos de C\+\+ desde y hacia IJW \(**\/clr\)** o código nativo.  Para obtener más información, vea [Advertencia del compilador \(nivel 2\) C4412](../Topic/Compiler%20Warning%20\(level%202\)%20C4412.md).  
  
## Consideraciones de arquitectura  
 Algunas de las limitaciones de los ensamblados MSIL puros indicadas en [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md) tienen implicaciones de alto nivel en el diseño de aplicaciones y en la estrategia de migración.  La más notable, a diferencia de los ensamblados mixtos, es que los ensamblados MSIL puros no tienen compatibilidad completa con los módulos no administrados.  
  
 Los ensamblados MSIL puros pueden llamar a funciones no administradas, pero no pueden ser llamados por funciones no administradas.  Como resultado, MSIL puro es mejor candidato para código de cliente que utilice funciones no administradas que para código de servidor que sea utilizado en funciones no administradas.  Si la funcionalidad contenida en un ensamblado MSIL puro va a ser utilizada en funciones no administradas, se debe usar un ensamblado mixto como capa de interfaz.  
  
 Las aplicaciones que utilizan ATL o MFC no son buenas candidatas para migración a MSIL puro, ya que estas bibliotecas no son compatibles con esta versión.  Igualmente, [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] contiene archivos de encabezado que no se compilan en **\/clr:pure**.  
  
 Aunque los ensamblados MSIL puros pueden llamar a funciones no administradas, esta capacidad se limita a las funciones de estilo C simples.  El uso de API no administradas más complejas probablemente requiere que se exponga la funcionalidad no administrada en forma de interfaz COM, o un ensamblado mixto que pueda actuar como interfaz entre los componentes MSIL puro y no administrados.  El uso de una capa de ensamblado mixto es la única forma de utilizar funciones no administradas que tomen funciones de devolución de llamada, por ejemplo, cuando un ensamblado puro no puede proporcionar una función invocable nativa para usarla como función de devolución de llamada.  
  
## Dominios de aplicación y convenciones de llamada  
 Aunque los ensamblados MSIL puros pueden utilizar la funcionalidad no administrada, las funciones y los datos estáticos se tratan de manera diferente.  En los ensamblados puros, las funciones se implementan con la convención de llamada [\_\_clrcall](../cpp/clrcall.md) y los datos estáticos se almacenan por dominio de aplicación.  Esto difiere de lo predeterminado para los ensamblados mixtos y no administrados, que usan la convención de llamada [\_\_cdecl](../cpp/cdecl.md) para las funciones y almacenan los datos estáticos por proceso.  
  
 En el contexto de MSIL puro \(y código comprobable compilado con \/clr:safe\), estas opciones predeterminadas son transparentes, ya que [\_\_clrcall](../cpp/clrcall.md) es la convención de llamada predeterminada de CLR y los dominios de aplicación son el ámbito nativo para los datos estáticos y globales en las aplicaciones de .NET.  Sin embargo, en la interfaz con componentes no administrados o mixtos, el tratamiento distinto de funciones y datos globales puede producir problemas.  
  
 Por ejemplo, si un componente MSIL puro va a llamar a funciones en un archivo DLL no administrado o mixto, se utilizará un archivo de encabezado correspondiente al DLL para compilar el ensamblado puro.  Sin embargo, a menos que se indique explícitamente la convención de llamada para cada función en el encabezado, se supondrá que es siempre [\_\_clrcall](../cpp/clrcall.md).  Esto producirá posteriormente errores en tiempo de ejecución, ya que es probable que estas funciones se implementen con la convención [\_\_cdecl](../cpp/cdecl.md).  Las funciones del archivo de encabezado no administrado se pueden marcar explícitamente como [\_\_cdecl](../cpp/cdecl.md), o el código fuente del archivo DLL completo se debe recompilar en **\/clr:pure**.  
  
 Del mismo modo, se supone que los punteros a función señalan a funciones [\_\_clrcall](../cpp/clrcall.md) en la compilación **\/clr:pure**.  Estos también se deben agregar explícitamente con la convención de llamada correcta.  
  
 Para obtener más información, vea [Dominios de aplicación y Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md).  
  
## Limitaciones de la vinculación  
 El vinculador de Visual C\+\+ no intentará vincular archivos OBJ mixtos y puros, ya que el ámbito de almacenamiento y las convenciones de llamada son diferentes.  
  
## Vea también  
 [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md)