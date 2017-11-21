---
title: 'Hstring:: operator! = (operador) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs: C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f7042b7ade41fe20d003a50e2d44360f2d74754
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="hstringoperator-operator"></a>HString::Operator!= (Operador)
Indica si los dos parámetros no son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator!=( const HString& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HStringReference& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HStringReference& rhs) throw()  
  
inline bool operator!=( const HSTRING& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HSTRING& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs`puede ser un objeto HString o HStringReference, o bien un controlador HSTRING.  
  
 `rhs`  
 El segundo parámetro para comparar.`rhs` puede ser un objeto HString o HStringReference, o bien un controlador HSTRING.  
  
## <a name="return-value"></a>Valor devuelto  
 Es `true` si los parámetros `lhs` y `rhs` no son iguales; en caso contrario, es `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)