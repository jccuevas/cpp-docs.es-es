---
title: "Bibliotecas estáticas (C++ / CX) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcd69fc00a44bdc0d8259a4a21d31c83ee5c6258
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)
Una biblioteca estática que se utiliza en una aplicación de la plataforma Universal de Windows (UWP) puede contener código de C++ conforme a normas ISO, incluyendo tipos STL y también llama a las API de Win32 no excluidas de la plataforma de aplicación de Windows en tiempo de ejecución. Una biblioteca estática utiliza componentes de Windows en tiempo de ejecución y puede crear componentes de Windows Runtime con ciertas restricciones.  
  
## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Para crear una biblioteca estática para su uso en una aplicación de UWP  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. En **Visual C++** > **universales de Windows** elegir **biblioteca estática (Windows Universal)**.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el **propiedades** cuadro de diálogo, en la **propiedades de configuración** > **C/C++** , establezca **usar Windows en tiempo de ejecución extensión** a **Sí (/ZW)**.  
  
 Cuando se compila una nueva biblioteca estática, si realiza una llamada a una API de Win32 excluida para aplicaciones UWP, el compilador generará el error C3861, "No se encontró el identificador". Para buscar un método alternativo que es compatible con el tiempo de ejecución de Windows, vea [alternativas a las API de Windows en las aplicaciones UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Si agrega un proyecto de biblioteca estática de C++ a una solución de aplicación UWP, es posible que deba actualizar la configuración de las propiedades del proyecto de biblioteca para que la propiedad de soporte técnico UWP se establece en **Sí**. Sin esta configuración, el código se compila y vincula, pero un error que se produce al intentar comprobar la aplicación para Microsoft Store. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.  
  
 Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:  
  
> **Advertencia LNK4264:** almacenamiento de un archivo objeto compilado con/ZW en una biblioteca estática; tenga en cuenta que, al crear tipos en tiempo de ejecución de Windows no se recomienda para vincular con una biblioteca estática que contiene los metadatos en tiempo de ejecución de Windows.  
  
 Puede ignorar la advertencia solo si la biblioteca estática no está produciendo componentes en tiempo de ejecución de Windows que se utilizan fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, se debe implementar cualquier componente de tiempo de ejecución de Windows está diseñado para su uso por otros componentes o aplicaciones en una biblioteca de vínculos dinámicos (DLL).  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento y cálculo de referencias](../cppcx/threading-and-marshaling-c-cx.md)