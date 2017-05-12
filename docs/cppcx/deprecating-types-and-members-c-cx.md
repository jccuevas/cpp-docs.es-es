---
title: "Dejar en desuso tipos y miembros (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Dejar en desuso tipos y miembros (C++/CX)
En C\+\+\/CX, el atributo [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] permite marcar como desusados los tipos y miembros de [Deprecated](http://msdn.microsoft.com/es-es/8b02ad36-3b5f-4361-888b-e6a99040e57c) para los productores y los consumidores. Si utilizas una API a la que se ha aplicado este atributo, obtienes un mensaje de advertencia en tiempo de compilación que indica que la API está desusada y que te recomienda una API alternativa. Puedes aplicar este atributo en tus propios tipos y métodos públicos, así como proporcionar tus propios mensajes personalizados.  
  
> [!CAUTION]
>  El atributo [Deprecated](http://msdn.microsoft.com/es-es/8b02ad36-3b5f-4361-888b-e6a99040e57c) solo se utiliza con tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. En las clases y miembros de C\+\+ estándar, usa [\_\_declspec\(deprecated\)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar como desusadas tus propias API públicas, por ejemplo, en un componente de Windows en tiempo de ejecución. El segundo parámetro, de tipo [Windows:Foundation::Metadata::DeprecationType](http://msdn.microsoft.com/es-es/ee01e63d-37d0-4273-accc-fca174f88bfa), especifica si la API se está marcando como desusada o se está quitando. Actualmente, solo se admite el valor DeprecationType::Deprecated. El tercer parámetro del atributo especifica el objeto [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/es-es/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) al que se aplica el atributo.  
  
```  
  
namespace wfm = Windows::Foundation::Metadata; public ref class Bicycle sealed { public: property double Speed; [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)] double ComputeAngularVelocity(); };  
```  
  
## Destinos admitidos  
 En la tabla siguiente se enumeran las construcciones a las que se puede aplicar el atributo Deprecated:  
  
||  
|-|  
|Control XAML|  
|delegado|  
|evento|  
|campo de enumeración|  
|enum|  
|struct|  
|método|  
|clase|  
|interfaz|  
|propiedad|  
|campo de struct|  
|constructor parametrizado|  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)