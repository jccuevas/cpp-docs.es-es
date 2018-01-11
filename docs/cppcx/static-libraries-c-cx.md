---
title: "Bibliotecas estáticas (C++ / CX) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a68475447ed520298b0eab7949386c2e8d078ac6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)
Una biblioteca estática que se utiliza en una aplicación de la plataforma Universal de Windows puede contener código C++ conforme a normas ISO, incluyendo los tipos STL y también llama a las API de Win32 no excluidas de la plataforma de aplicación de plataforma Universal de Windows. Una biblioteca estática utiliza componentes de Windows en tiempo de ejecución y puede crear componentes de Windows Runtime con ciertas restricciones.  
  
## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas  
  
#### <a name="to-create-a-static-library-for-use-in-a-universal-windows-platform-app"></a>Para crear una biblioteca estática para su uso en una aplicación de plataforma Universal de Windows  
  
1.  En la barra de menús, elija **archivo** > **New** > **proyecto** > **biblioteca estática en blanco** para Windows Universal aplicaciones de la plataforma.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el **propiedades** cuadro de diálogo, en la **propiedades de configuración** > **General** página, establezca la compatibilidad con aplicaciones de plataforma Universal de Windows en  **Sí**.  
  
3.  En el **propiedades de configuración** > **C/C++** , establezca **Consume** en tiempo de ejecución de Windows **extensión** a **Sí (/ZW)**.  
  
 Cuando se compila una nueva biblioteca estática, si realiza una llamada a una API de Win32 excluida para aplicaciones de la plataforma Universal de Windows, el compilador generará el error C3861, "No se encontró el identificador". Para buscar un método alternativo que es compatible con el tiempo de ejecución de Windows, vea [alternativas a las API de Windows en aplicaciones de la tienda de Windows](http://msdn.microsoft.com/en-us/75568012-61e0-41cc-a4df-c698f54f21ec).  
  
 Si agrega un proyecto de biblioteca estática de C++ a una solución de aplicación de plataforma Universal de Windows, es posible que deba actualizar la configuración de las propiedades del proyecto de biblioteca para que la propiedad de compatibilidad de plataforma Universal de Windows está establecida en **Sí**. Sin este valor de configuración, el código se compila y se vincula, pero se produce un error si intentas comprobar la aplicación para la [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.  
  
 Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:  
  
> **Advertencia LNK4264:** almacenamiento de un archivo objeto compilado con/ZW en una biblioteca estática; tenga en cuenta que, al crear tipos en tiempo de ejecución de Windows no se recomienda para vincular con una biblioteca estática que contiene los metadatos en tiempo de ejecución de Windows.  
  
 Puede ignorar la advertencia solo si la biblioteca estática no está produciendo componentes en tiempo de ejecución de Windows que se utilizan fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, se debe implementar cualquier componente de tiempo de ejecución de Windows está diseñado para su uso por otros componentes o aplicaciones en una biblioteca de vínculos dinámicos (DLL).  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento y cálculo de referencias](../cppcx/threading-and-marshaling-c-cx.md)