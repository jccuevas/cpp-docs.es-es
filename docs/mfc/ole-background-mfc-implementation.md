---
title: "Nociones OLE: Implementación de MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IMarshall
- IMoniker
dev_langs: C++
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 530cc14135fd38e2177e00dc87974e96ffe24b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background-mfc-implementation"></a>Nociones de OLE: Implementación de MFC
Debido al tamaño y complejidad de la API básica de OLE, llamarla directamente para programar aplicaciones OLE puede ser muy lento. El objetivo de la implementación de la biblioteca Microsoft Foundation Class de OLE es reducir la cantidad de trabajo que tiene que hacer para escribir aplicaciones compatibles con OLE, completa.  
  
 En este artículo se explica las partes de la API de OLE que no se ha implementado dentro de MFC. También se explica cómo lo que está implementado asigna a la sección OLE del SDK de Windows.  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Algunas partes de OLE no implementadas por la biblioteca de clases  
 Algunas características de OLE e interfaces no se proporcionan directamente por MFC. Si desea usar estas características, puede llamar a la API de OLE directamente.  
  
 IMoniker (interfaz)  
 El `IMoniker` interfaz está implementada por la biblioteca de clases (por ejemplo, el `COleServerItem` clase), pero no se ha expuesto previamente al programador. Para obtener más información acerca de esta interfaz, vea OLE Moniker implementaciones en la sección OLE del SDK de Windows. Sin embargo, también vea clase [CMonikerFile](../mfc/reference/cmonikerfile-class.md) y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
 Interfaces IUnknown e IMarshal  
 El **IUnknown** interfaz está implementada por la biblioteca de clases, pero no se expone al programador. El **IMarshal** interfaz no está implementada por la biblioteca de clases, pero se usa internamente. Servidores de automatización creados con la biblioteca de clases ya tienen funciones integradas el cálculo de referencias.  
  
 Docfiles (archivos compuestos)  
 Archivos compuestos parcialmente son compatibles con la biblioteca de clases. Ninguna de las funciones que manipulan directamente archivos compuestos más allá de creación se admiten. MFC utiliza la clase **COleFileStream** para admitir la manipulación de secuencias con funciones estándar de archivo. Para obtener más información, vea el artículo [contenedores: archivos compuestos](../mfc/containers-compound-files.md).  
  
 Servidores en proceso y controladores de objeto  
 Servidores en proceso y controladores de objeto permiten la implementación de edición visual de datos u objetos de modelo de objetos componentes (COM) completo en una biblioteca de vínculos dinámicos (DLL). Para ello, puede implementar el archivo DLL mediante una llamada a la API de OLE directamente. Sin embargo, si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede usar el Asistente para aplicaciones para convertir al servidor en un servidor en proceso y colocarlo en un archivo DLL. Para obtener más información acerca de estos temas, consulte [servidores de automatización](../mfc/automation-servers.md).  
  
> [!TIP]
>  La manera más fácil de implementar un servidor de automatización es colocarlo en un archivo DLL. MFC admite este enfoque.  
  
 Para obtener más información sobre cómo las clases OLE de Microsoft Foundation implementan interfaces OLE, vea las notas técnicas de MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), y [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
## <a name="see-also"></a>Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)

