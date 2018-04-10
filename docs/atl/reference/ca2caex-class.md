---
title: Clase CA2CAEX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f579716cff70d0c9f20ea0fa0133dcb4d86c8db3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ca2caex-class"></a>Clase CA2CAEX
Esta clase se utiliza con macros de conversión de cadena `CA2CTEX` y `CT2CAEX`y la definición de tipo **CA2CA**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](#ca2caex)|El constructor.|  
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Operador de conversión.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CA2CAEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que sea necesaria una funcionalidad adicional, utilice `CA2CTEX`, `CT2CAEX`, o **CA2CA** en su propio código.  
  
 Esta clase es segura utilizar en bucles y no desbordarán la pila. Las macros y clases de conversión de ATL utilizarán de forma predeterminada la página de código ANSI del subproceso actual para la conversión.  
  
 Las macros siguientes se basan en esta clase:  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 La siguiente definición de tipo se basa en esta clase:  
  
- **CA2CA**  
  
 Para obtener una descripción de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlconv.h  
  
##  <a name="ca2caex"></a>CA2CAEX::CA2CAEX  
 El constructor.  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `psz`  
 La cadena de texto que se va a convertir.  
  
 `nCodePage`  
 No se utiliza en esta clase.  
  
### <a name="remarks"></a>Comentarios  
 Crea el búfer necesario para la traducción.  
  
##  <a name="dtor"></a>CA2CAEX:: ~ CA2CAEX  
 Destructor.  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el búfer asignado.  
  
##  <a name="m_psz"></a>CA2CAEX::m_psz  
 El miembro de datos que almacena la cadena de origen.  
  
```
LPCSTR m_psz;
```  
  
##  <a name="operator_lpcstr"></a>CA2CAEX::operator LPCSTR  
 Operador de conversión.  
  
```  
operator LPCSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cadena de texto como tipo `LPCSTR`.  
  
## <a name="see-also"></a>Vea también  
 [Clase CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Clase CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Clase CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Clase CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
