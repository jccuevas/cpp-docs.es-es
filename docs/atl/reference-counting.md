---
title: Recuento (ATL) de referencias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e0ce8b2cc412c576b0eded9662d8e70b34cf2ec
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850818"
---
# <a name="reference-counting"></a>Recuento de referencias
El propio COM no automáticamente intenta quitar un objeto de memoria cuando piensa que el objeto ya no está usando. En su lugar, el programador de objetos debe quitar el objeto sin usar. El programador determina si un objeto se puede quitar según un recuento de referencias.  
  
 COM utiliza el `IUnknown` métodos, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) y [versión](http://msdn.microsoft.com/library/windows/desktop/ms682317), para administrar el recuento de referencias de las interfaces en un objeto. Las reglas generales para llamar a estos métodos son:  
  
-   Cada vez que un cliente recibe un puntero de interfaz `AddRef` debe llamarse en la interfaz.  
  
-   Cada vez que el cliente ha terminado de utilizar el puntero de interfaz, debe llamar a `Release`.  
  
 En una implementación simple, cada `AddRef` llamar a incrementos y cada `Release` llamar reduce una variable de contador dentro del objeto. Cuando el recuento vuelve a cero, la interfaz ya no tiene ningún usuario y es gratuita para quitarse de la memoria.  
  
 Recuento de referencias también se puede implementar para que se cuentan todas las referencias al objeto (no a una interfaz individual). En este caso, cada `AddRef` y `Release` llamar a los delegados en una implementación central del objeto, y `Release` libera el objeto completo cuando su recuento de referencias llega a cero.  
  
> [!NOTE]
>  Cuando un `CComObject`-derivado objeto se construye utilizando el **nuevo** operador, el recuento de referencias es 0. Por lo tanto, una llamada a `AddRef` se deben realizar después de crear correctamente el `CComObject`-objeto derivado.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Administrar la duración de objeto a través de un recuento de referencias](http://msdn.microsoft.com/library/windows/desktop/ms687260)

