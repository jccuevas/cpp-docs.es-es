---
title: IUnknown | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IUnknown
dev_langs: C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e46ee55412c591558389bb7ac42116431eaaa6ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) es la interfaz base de todas las demás interfaces COM.  Esta interfaz define tres métodos: [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317). [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) permite a un usuario de la interfaz solicitar al objeto un puntero a otro de sus interfaces. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317) implementar recuento de referencias en la interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [IUnknown y herencia de interfaz](http://msdn.microsoft.com/library/windows/desktop/ms692713)

