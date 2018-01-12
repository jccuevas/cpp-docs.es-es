---
title: nonextensible (atributo) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nonextensible
dev_langs: C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af16748bb3b2048ce854ccc7a03b2400039184a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nonextensible-attribute"></a>nonextensible (atributo)
Si no se extiende una interfaz dual en tiempo de ejecución (es decir, si no se ofrecen métodos ni propiedades a través de **IDispatch:: Invoke** que no están disponibles a través de la vtable), debe aplicar la **nonextensible** atributo a la definición de interfaz. Este atributo proporciona información para idiomas de cliente (por ejemplo, Visual Basic) que puede usarse para habilitar la comprobación de código completo en tiempo de compilación. Si no se proporciona este atributo, podrían quedar ocultos errores en el código de cliente hasta el tiempo de ejecución.  
  
 Para obtener más información sobre la **nonextensible** atributo y un ejemplo, vea [nonextensible](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Vea también  
 [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)

