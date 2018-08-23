---
title: Bibliotecas estáticas (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb69b65d78b6369d872fd6f953f6ddde382c21b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602294"
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)
Una biblioteca estática que se usa en una aplicación de plataforma Universal de Windows (UWP) puede contener código de la norma ISO C++, incluidos los tipos STL y también las llamadas a API de Win32 que no se excluyen de la plataforma de aplicaciones de Windows en tiempo de ejecución. Una biblioteca estática utiliza componentes de Windows en tiempo de ejecución y puede crear componentes de Windows en tiempo de ejecución con ciertas restricciones.  
  
## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Para crear una biblioteca estática para su uso en una aplicación para UWP  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. En **Visual C++** > **Windows Universal** elija **biblioteca estática (Windows Universal)**.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el **propiedades** cuadro de diálogo el **propiedades de configuración** > **C o C++** , establezca **usar Windows en tiempo de ejecución extensión** a **Sí (/ZW)**.  
  
 Cuando se compila una nueva biblioteca estática, si realiza una llamada a una API de Win32 excluida para las aplicaciones para UWP, el compilador producirá el error C3861, "No se encontró el identificador". Para buscar un método alternativo que es compatible con el tiempo de ejecución de Windows, consulte [alternativas a las API de Windows en aplicaciones para UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Si agrega un proyecto de biblioteca estática de C++ a una solución de aplicación para UWP, es posible que deba actualizar los valores de las propiedades del proyecto de biblioteca para que se establece la propiedad de soporte técnico UWP en **Sí**. Sin esta configuración, el código se compila y vínculos, pero un error que se produce cuando se intenta comprobar la aplicación para la Microsoft Store. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.  
  
 Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:  
  
> **warning LNK4264:** almacenamiento de un archivo objeto compilado con /ZW en una biblioteca estática; tenga en cuenta que, al crear tipos en tiempo de ejecución de Windows no se recomienda para vincular con una biblioteca estática que contiene los metadatos de Windows en tiempo de ejecución.  
  
 Puede ignorar la advertencia solo si la biblioteca estática no está generando los componentes de Windows en tiempo de ejecución que se utilizan fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, se debe implementar cualquier componente de Windows en tiempo de ejecución que está pensado para su uso por otros componentes o aplicaciones en una biblioteca de vínculos dinámicos (DLL).  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)