---
title: "CComEnumImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComEnumImpl"
  - "ATL::CComEnumImpl"
  - "CComEnumImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumImpl class"
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComEnumImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona la implementación de una interfaz COM de enumerador donde los elementos enumerados se almacenan en una matriz.  
  
## Sintaxis  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy  
>  
class ATL_NO_VTABLE CComEnumImpl :   
   public Base  
```  
  
#### Parámetros  
 `Base`  
 Una interfaz COM de enumerador \(\).  
  
 `piid`  
 Un puntero al identificador de la interfaz de la interfaz del enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz del enumerador.  
  
 `Copy`  
 [clase de directiva de copia](../../atl/atl-copy-policy-classes.md)homogéneo.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](../Topic/CComEnumImpl::CComEnumImpl.md)|el constructor.|  
|[CComEnumImpl::~CComEnumImpl](../Topic/CComEnumImpl::~CComEnumImpl.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::Clone](../Topic/CComEnumImpl::Clone.md)|la implementación de [:: clon](https://msdn.microsoft.com/en-us/library/ms690336.aspx).|  
|[CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)|Inicializa el enumerador.|  
|[CComEnumImpl::Next](../Topic/CComEnumImpl::Next.md)|la implementación de [:: Siguiente](https://msdn.microsoft.com/en-us/library/ms695273.aspx).|  
|[CComEnumImpl::Reset](../Topic/CComEnumImpl::Reset.md)|la implementación de [:: Restablecer](https://msdn.microsoft.com/en-us/library/ms693414.aspx).|  
|[CComEnumImpl::Skip](../Topic/CComEnumImpl::Skip.md)|la implementación de [:: Omitir](https://msdn.microsoft.com/en-us/library/ms690392.aspx).|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComEnumImpl::m\_begin](../Topic/CComEnumImpl::m_begin.md)|Un puntero al primer elemento de la matriz.|  
|[CComEnumImpl::m\_dwFlags](../Topic/CComEnumImpl::m_dwFlags.md)|Indicadores de copia pasados con `Init`.|  
|[CComEnumImpl::m\_end](../Topic/CComEnumImpl::m_end.md)|Un puntero a la ubicación simplemente más allá del último elemento de la matriz.|  
|[CComEnumImpl::m\_iter](../Topic/CComEnumImpl::m_iter.md)|Un puntero al elemento actual en la matriz.|  
|[CComEnumImpl::m\_spUnk](../Topic/CComEnumImpl::m_spUnk.md)|El puntero de **IUnknown** del objeto que proporciona la colección que es enumerada.|  
  
## Comentarios  
 `CComEnumImpl` proporciona la implementación de una interfaz COM de enumerador donde los elementos enumerados se almacenan en una matriz.  Esta clase es análoga a la clase de `IEnumOnSTLImpl` , que proporciona una implementación de una interfaz de enumerador basada en un contenedor de STL.  
  
> [!NOTE]
>  Para obtener información sobre otras diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`, vea [CComEnumImpl:: Iniciar](../Topic/CComEnumImpl::Init.md).  
  
 Normalmente, no necesitará crear dispone de la clase enumerator derivando de esta implementación de la interfaz.  Si desea utilizar un enumerador ATL\-proporcionado basado en una matriz, es más común crear una instancia de [CComEnum](../../atl/reference/ccomenum-class.md).  
  
 Sin embargo, si necesita proporcionar un enumerador personalizado \(por ejemplo, uno que expone interfaces además de la interfaz del enumerador\), puede derivar de esta clase.  En esta situación, es probable que necesite reemplazar el método de [CComEnumImpl:: clon](../Topic/CComEnumImpl::Clone.md) para proporcionar dispone de la implementación.  
  
 Para obtener más información, vea [Colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComEnumImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum Class](../../atl/reference/ccomenum-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)