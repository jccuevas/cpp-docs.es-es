---
title: "Integraci&#243;n de CLR (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# Integraci&#243;n de CLR (C++/CX)
Algunos tipos [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] reciben un tratamiento especial en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] y los lenguajes basados en Common Language Runtime \(CLR\). En este artículo se describe la manera en que varios tipos de un lenguaje se asignan a otro lenguaje. Por ejemplo, CLR asigna Windows.Foundation.IVector to System.Collections.IList, Windows.Foundation.IMap to System.Collections.IDictionary, etc. De forma similar, [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] asigna especialmente tipos como Platform::Delegate y Platform::String.  
  
## Asignación de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] a [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 Cuando [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] lee un archivo de metadatos \(.winmd\) de Windows, el compilador asigna automáticamente espacios de nombres [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] comunes y tipos a tipos y espacios de nombres [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]. Por ejemplo, el tipo [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] numérico `UInt32` se asigna automáticamente a `default::uint32`.  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] asigna varios otros tipos [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] al espacio de nombres **Platform**. Por ejemplo, el controlador HSTRING **Windows::Foundation**, que representa una cadena de texto Unicode de solo lectura, se asigna a la clase [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::String`. Cuando una operación [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] devuelve un HRESULT de error, se asigna a [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::Exception`. Para obtener más información, consulta [Built\-in Types](http://msdn.microsoft.com/es-es/acc196fd-09da-4882-b554-6c94685ec75f).  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] también asigna determinados tipos en espacios de nombres [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] para mejorar la funcionalidad del tipo. Para estos tipos, [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] ofrece métodos y constructores auxiliares que son específicos de C\+\+ y que no están disponibles en el archivo .winmd estándar del tipo.  
  
 En las listas siguientes se muestran estructuras de valor que admiten nuevos métodos auxiliares y constructores. Si ha escrito código anteriormente que usa listas de inicialización de estructuras, cámbielo para usar los constructores recién agregados.  
  
 **Windows::Foundation**  
  
-   Punto  
  
-   Rect  
  
-   Tamaño  
  
 **Windows::UI**  
  
-   Color  
  
 **Windows::UI::XAML**  
  
-   CornerRadius  
  
-   Duración  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::XAML::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   Matrix  
  
 **Windows::UI::XAML::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## Asignación de CLR a [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 Cuando los compiladores de Visual C\+\+ o C\# leen un archivo .winmd, asignan automáticamente determinados tipos del archivo de metadatos a los tipos de CLR o [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] adecuados. Por ejemplo, en el CLR, la interfaz de IVector\<T\> se asigna a IList\<T\>. Pero en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], la interfaz de IVector\<T\> no se asigna a otro tipo.  
  
 IReference\<T\> en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] asigna a Nullable\<T\> en. NET.  
  
## Vea también  
 [Interoperar con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)