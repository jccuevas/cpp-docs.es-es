---
title: QueryInterface | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce14ebef3649cea78e8cf4315a62392cfa142152
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="queryinterface"></a>QueryInterface
Aunque hay mecanismos mediante el cual un objeto puede expresar la funcionalidad que proporciona estáticamente (antes de que se crean las instancias), el mecanismo COM fundamental es utilizar el **IUnknown** método llamado [QueryInterface ](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Cada interfaz se deriva de **IUnknown**, por lo que cada interfaz tiene una implementación de `QueryInterface`. Independientemente de la implementación, este método consulta un objeto mediante el IID de la interfaz a la que el llamador desea un puntero. Si el objeto admite esa interfaz, `QueryInterface` recupera un puntero a la interfaz, mientras se también llama a `AddRef`. De lo contrario, devuelve el **E_NOINTERFACE** código de error.  
  
 Tenga en cuenta que deben obedecer [recuento de referencias](../atl/reference-counting.md) reglas en todo momento. Si se llama a **versión** en un puntero de interfaz para reducir el recuento de referencias en cero, no debe usar ese puntero nuevo. En ocasiones, puede que necesite obtener una referencia débil a un objeto (es decir, puede que desee obtener un puntero a una de sus interfaces sin incrementar el recuento de referencias), pero no es aceptable para ello, llame a `QueryInterface` seguido  **Versión**. El puntero obtenido de manera no es válido y no debe usarse. Esto más fácil es evidente cuando [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) está definido, por lo que definir esta macro es una forma útil de errores de recuento de referencias de búsqueda.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [QueryInterface: Desplazarse por un objeto](http://msdn.microsoft.com/library/windows/desktop/ms687230)

