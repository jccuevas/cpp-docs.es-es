---
title: Clase CA2WEX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 93f3fdbd9c728dcaea0262cb774fe5891e6a9838
ms.lasthandoff: 03/31/2017

---
# <a name="ca2wex-class"></a>Clase CA2WEX
Esta clase se utiliza por las macros de conversión de cadena `CA2TEX`, `CA2CTEX`, `CT2WEX`, y `CT2CWEX`y la definición de tipo **CA2W**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parámetros  
 `t_nBufferLength`  
 El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|El constructor.|  
|[CA2WEX:: ~ CA2WEX](#dtor)|Destructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Operador de conversión.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|El búfer estático, usado para almacenar la cadena convertida.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que sea necesaria una funcionalidad adicional, utilice `CA2TEX`, `CA2CTEX`, `CT2WEX`, `CT2CWEX`, o **CA2W** en el código.  
  
 Esta clase contiene un búfer estático de tamaño fijo que se utiliza para almacenar el resultado de la conversión. Si el resultado es demasiado grande y no encaja en el búfer estático, la clase asigna memoria por medio de `malloc`, memoria que libera cuando el objeto se sale del ámbito. Esto garantiza que, a diferencia del texto macros de conversión disponibles en versiones anteriores de ATL, esta clase es segura utilizar en bucles y que no desbordamiento de la pila.  
  
 Si la clase intenta asignar memoria en la pila y se produce un error, llamará a `AtlThrow` con un argumento de **E_OUTOFMEMORY**.  
  
 De forma predeterminada, las macros y clases de conversión de ATL utilizan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar este comportamiento para una conversión concreta, especifique la página de códigos como segundo parámetro del constructor de la clase.  
  
 Las macros siguientes se basan en esta clase:  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 La siguiente definición de tipo se basa en esta clase:  
  
- **CA2W**  
  
 Para obtener una descripción de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlconv.h  
  
##  <a name="ca2wex"></a>CA2WEX::CA2WEX  
 El constructor.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `psz`  
 La cadena de texto que se va a convertir.  
  
 `nCodePage`  
 La página de códigos que se utiliza para realizar la conversión. Vea la descripción del parámetro de página de código para el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] función [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) para obtener más detalles.  
  
### <a name="remarks"></a>Comentarios  
 Asigna el búfer utilizado en el proceso de traducción.  
  
##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX  
 Destructor.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el búfer asignado.  
  
##  <a name="m_psz"></a>CA2WEX::m_psz  
 El miembro de datos que almacena la cadena de origen.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer  
 El búfer estático, usado para almacenar la cadena convertida.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR  
 Operador de conversión.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cadena de texto como tipo **LPWSTR.**  
  
## <a name="see-also"></a>Vea también  
 [Clase CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Clase CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Clase CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Clase CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)

