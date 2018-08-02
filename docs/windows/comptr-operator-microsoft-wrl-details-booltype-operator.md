---
title: 'Comptr:: operator booltype (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a4ec737c3f24899e50220c3e862283b88a826b9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461169"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType (Operador)
Indica si un **ComPtr** administra la duración del objeto de una interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si una interfaz que está asociada a este **ComPtr**, la dirección de la [Boolstruct](../windows/boolstruct-member-data-member.md) miembro de datos; de lo contrario, **nullptr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)   
 [ComPtr::Get (método)](../windows/comptr-get-method.md)