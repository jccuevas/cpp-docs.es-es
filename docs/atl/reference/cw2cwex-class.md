---
title: Clase CW2CWEX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a83f0fefed5e2393c303038346e3b84ec1a3d570
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cw2cwex-class"></a>Clase CW2CWEX
Esta clase se utiliza por las macros de conversión de cadena `CW2CTEX` y `CT2CWEX`y la definición de tipo `CW2W`.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::CW2CWEX](#cw2cwex)|El constructor.|  
|[CW2CWEX:: ~ CW2CWEX](#dtor)|Destructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|Operador de conversión.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2CWEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que sea necesaria una funcionalidad adicional, utilice `CW2CTEX`, `CT2CWEX`, o `CW2W` en el código.  
  
 Esta clase es segura utilizar en bucles y no desbordarán la pila. De forma predeterminada, las macros y clases de conversión de ATL utilizan la página de códigos ANSI del subproceso actual para la conversión.  
  
 Las macros siguientes se basan en esta clase:  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 La siguiente definición de tipo se basa en esta clase:  
  
- `CW2W`  
  
 Para obtener una descripción de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlconv.h  
  
##  <a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
 El constructor.  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `psz`  
 La cadena de texto que se va a convertir.  
  
 `nCodePage`  
 La página de códigos. No se utiliza en esta clase.  
  
### <a name="remarks"></a>Comentarios  
 Asigna el búfer utilizado en el proceso de traducción.  
  
##  <a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 Destructor.  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el búfer asignado.  
  
##  <a name="m_psz"></a>CW2CWEX::m_psz  
 El miembro de datos que almacena la cadena de origen.  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR  
 Operador de conversión.  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cadena de texto como tipo **LPCWSTR.**  
  
## <a name="see-also"></a>Vea también  
 [Clase CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Clase CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Clase CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Clase CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Clase CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
