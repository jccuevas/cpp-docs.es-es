---
title: ComPtr::Reset | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd2ce820367b15cb5dad8baf691a835499457a55
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870772"
---
# <a name="comptrreset"></a>ComPtr::Reset
Libera todas las referencias del puntero a la interfaz asociada a este ComPtr.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El número de referencias liberado, si existe.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)