---
title: "Bibliotecas est&#225;ticas (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# Bibliotecas est&#225;ticas (C++/CX)
Una biblioteca estática que se utiliza en una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] puede contener código en C\+\+ conforme a normas ISO, incluyendo los tipos STL, y también llama a las API de Win32 no excluidas de la plataforma de aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]. Una biblioteca estática utiliza componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y puede crear componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] con ciertas restricciones.  
  
## Crear bibliotecas estáticas  
  
#### Para crear una biblioteca estática para su uso en una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]  
  
1.  En la barra de menús, elige **Archivo** \> **Nuevo** \> **Proyecto** \> **Biblioteca estática en blanco** para aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)].  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el cuadro de diálogo **Propiedades**, en la página **Propiedades de configuración** \> **General**, establece la compatibilidad con aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] en **Sí**.  
  
3.  En la página **Propiedades de configuración** \> **C o C\+\+**, establezca **Consumir** [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] **extensión** en **Sí \(\/ZW\)**.  
  
 Cuando compiles una nueva biblioteca estática, si realizas una llamada a una API de Win32 excluida para las aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], el compilador producirá el error C3861, “No se encuentra el identificador”. Para buscar un método alternativo admitido para [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], vea [Alternatives to Windows APIs in Windows Store apps](http://msdn.microsoft.com/es-es/75568012-61e0-41cc-a4df-c698f54f21ec).  
  
 Si agregas un proyecto de biblioteca estática de C\+\+ a una solución de aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], es posible que tengas que actualizar los valores de configuración de propiedades del proyecto de biblioteca de manera que la propiedad de compatibilidad de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] esté establecida en **Sí**. Sin este valor de configuración, el código se compila y se vincula, pero se produce un error si intentas comprobar la aplicación para la [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.  
  
 Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:  
  
> **warning LNK4264:** almacenamiento de un archivo objeto compilado con \/ZW en una biblioteca estática; tenga en cuenta que, al crear tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], no se recomienda la vinculación con una biblioteca estática que contenga metadatos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 Puedes omitir la advertencia sin ningún problema solo si la biblioteca estática no está produciendo componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] que se utilizan fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] previstos para su uso por otros componentes o aplicaciones deben implementarse en una biblioteca de vínculos dinámicos \(DLL\).  
  
## Vea también  
 [Subprocesamiento y cálculo de referencias](../cppcx/threading-and-marshaling-c-cx.md)