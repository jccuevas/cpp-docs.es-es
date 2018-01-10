---
title: Clase CComAutoCriticalSection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d12abfceeebeb1cac89b510c14d7a9211173406e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomautocriticalsection-class"></a>Clase CComAutoCriticalSection
`CComAutoCriticalSection`Proporciona métodos para la obtención y liberación de propiedad de un objeto de sección crítica.  
  
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
 `CComAutoCriticalSection`es similar a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), excepto `CComAutoCriticalSection` automáticamente inicializa el objeto de sección crítica en el constructor.  
  
 Normalmente, se utiliza `CComAutoCriticalSection` a través de la `typedef` nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Hace referencia a este nombre `CComAutoCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.  

  
 El `Init` y `Term` métodos de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles al utilizar esta clase.  
  
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
 El destructor llama [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), lo cual permite liberar todos los recursos del sistema utilizados por el objeto de sección crítica.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)
