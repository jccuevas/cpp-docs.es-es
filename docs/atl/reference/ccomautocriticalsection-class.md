---
title: Clase CComAutoCriticalSection | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae0c3cd1d00ce83a4e952d60a978663bfa76f814
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357234"
---
# <a name="ccomautocriticalsection-class"></a>Clase CComAutoCriticalSection
`CComAutoCriticalSection` Proporciona métodos para la obtención y liberación de propiedad de un objeto de sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|El constructor.|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|Destructor.|  
  
## <a name="remarks"></a>Comentarios  
 `CComAutoCriticalSection` es similar a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), excepto `CComAutoCriticalSection` automáticamente inicializa el objeto de sección crítica en el constructor.  
  
 Normalmente, se utiliza `CComAutoCriticalSection` a través de la `typedef` nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Hace referencia a este nombre `CComAutoCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.  

  
 El `Init` y `Term` métodos de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles al utilizar esta clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection  
 El constructor.  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función de Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), que inicializa el objeto de sección crítica.  
  
##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 Destructor.  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor llama [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), lo cual permite liberar todos los recursos del sistema utilizados por el objeto de sección crítica.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)
