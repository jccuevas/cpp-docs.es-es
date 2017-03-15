---
title: Clase CA2CAEX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CA2CAEX
- ATL.CA2CAEX<t_nBufferLength>
- ATLCONV/CA2CAEX
- ATL::CA2CAEX<t_nBufferLength>
- ATL::CA2CAEX
- CA2CAEX
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f104a62144e7fd8ac802c27dfe940a7f96d0e79a
ms.lasthandoff: 02/24/2017

---
# <a name="ca2caex-class"></a>Clase CA2CAEX
Esta clase es utilizada por las macros de conversión de cadena `CA2CTEX` y `CT2CAEX`y la definición de tipo **CA2CA**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer utilizado en el proceso de traducción. La longitud predeterminada es 128 bytes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](#ca2caex)|El constructor.|  
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|Operador de conversión.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2CAEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que se requiere funcionalidad adicional, use `CA2CTEX`, `CT2CAEX`, o **CA2CA** en su propio código.  
  
 Esta clase es segura utilizar en bucles y no desbordarán la pila. Las macros y clases de conversión de ATL utilizarán de forma predeterminada la página de código ANSI del subproceso actual para la conversión.  
  
 Las macros siguientes se basan en esta clase:  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 La siguiente definición de tipo se basa en esta clase:  
  
- **CA2CA**  
  
 Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadenas de MFC y ATL](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863).  
  
## <a name="example"></a>Ejemplo  
 Consulte [Macros de conversión de cadenas de MFC y ATL](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863) para obtener un ejemplo del uso de estas macros de conversión de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlconv.h  
  
##  <a name="a-nameca2caexa--ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX::CA2CAEX  
 El constructor.  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `psz`  
 La cadena de texto que se va a convertir.  
  
 `nCodePage`  
 No utilizado en esta clase.  
  
### <a name="remarks"></a>Comentarios  
 Crea el búfer necesario para la traducción.  
  
##  <a name="a-namedtora--ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX:: ~ CA2CAEX  
 Destructor.  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el búfer asignado.  
  
##  <a name="a-namempsza--ca2caexmpsz"></a><a name="m_psz"></a>CA2CAEX::m_psz  
 El miembro de datos que almacena la cadena de origen.  
  
```
LPCSTR m_psz;
```  
  
##  <a name="a-nameoperatorlpcstra--ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::operator LPCSTR  
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
 [Información general de la clase](../../atl/atl-class-overview.md)

