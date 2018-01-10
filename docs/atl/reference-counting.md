---
title: Referencia de recuento (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: be6aff46df500a55665f85f6f462514985885b9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="reference-counting"></a>Recuento de referencias
COM en sí mismo no automáticamente intenta quitar un objeto de la memoria cuando piensa que el objeto ya no está usándola. En su lugar, el programador de objetos debe quitar el objeto no utilizado. El programador determina si un objeto se puede quitar en función de un recuento de referencias.  
  
 COM usa la **IUnknown** métodos, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), para administrar el recuento de referencias de las interfaces en un objeto. Las reglas generales para llamar a estos métodos son:  
  
-   Cada vez que un cliente recibe un puntero de interfaz, `AddRef` se debe llamar en la interfaz.  
  
-   Cada vez que el cliente ha terminado de usar el puntero de interfaz, debe llamar a **versión**.  
  
 En una implementación simple, cada `AddRef` llamar a incrementos y cada uno de ellos **versión** llamadas disminuye una variable de contador dentro del objeto. Cuando el recuento vuelve a cero, la interfaz ya no tiene ningún usuario y puede quitarse de la memoria.  
  
 Recuento de referencias también se puede implementar para que se cuentan todas las referencias al objeto (no a una interfaz individual). En este caso, cada `AddRef` y **versión** llamar a delegados para una implementación central en el objeto, y **versión** libera el objeto completo cuando su recuento de referencias llega a cero.  
  
> [!NOTE]
>  Cuando un `CComObject`-objeto derivado se construye utilizando el **nueva** (operador), el recuento de referencias es 0. Por lo tanto, una llamada a `AddRef` se deben realizar después de crear correctamente el `CComObject`-objeto derivado.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Administrar la duración de los objetos a través de recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms687260)

