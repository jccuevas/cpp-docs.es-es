---
title: Clase CComAutoCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 9f58a4cfd02af09a05b625a7e02b574b672adade
ms.lasthandoff: 02/24/2017

---
# <a name="ccomautocriticalsection-class"></a>Clase CComAutoCriticalSection
`CComAutoCriticalSection`Proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|El constructor.|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|Destructor.|  
  
## <a name="remarks"></a>Comentarios  
 `CComAutoCriticalSection`es similar a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), excepto `CComAutoCriticalSection` automáticamente inicializa el objeto de sección crítica en el constructor.  
  
 Normalmente, se utiliza `CComAutoCriticalSection` a través de la `typedef` nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Este nombre hace referencia a `CComAutoCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.  

  
 El `Init` y `Term` métodos de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles cuando se utiliza esta clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection  
 El constructor.  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función de Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), que inicializa el objeto de sección crítica.  
  
##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 Destructor.  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor llama [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), que libera todos los recursos del sistema utilizados por el objeto de sección crítica.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

