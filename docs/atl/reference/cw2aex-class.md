---
title: Clase CW2AEX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13b6531dd1299235a125b1c25b0b1d84781755ed
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217845"
---
# <a name="cw2aex-class"></a>Clase CW2AEX
Esta clase se utiliza por las macros de conversión de cadena CT2AEX, CW2TEX, CW2CTEX y CT2CAEX y la definición de tipo CW2A.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>Parámetros  
 *t_nBufferLength*  
 El tamaño del búfer usado en el proceso de traducción. La longitud predeterminada es de 128 bytes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](#cw2aex)|El constructor.|  
|[CW2AEX:: ~ CW2AEX](#dtor)|Destructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::operator LPSTR](#operator_lpstr)|Operador de conversión.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CW2AEX::m_psz](#m_psz)|El miembro de datos que almacena la cadena de origen.|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|El búfer estático, utilizado para almacenar la cadena convertida.|  
  
## <a name="remarks"></a>Comentarios  
 A menos que se requiere una funcionalidad adicional, use CT2AEX, CW2TEX, CW2CTEX, CT2CAEX o CW2A en el código.  
  
 Esta clase contiene un búfer estático de tamaño fijo que se usa para almacenar el resultado de la conversión. Si el resultado es demasiado grande para caber en el búfer estático, la clase asigna memoria mediante **malloc**, libere la memoria cuando el objeto queda fuera del ámbito. Esto garantiza que, a diferencia del texto macros de conversión disponibles en versiones anteriores de ATL, esta clase es segura para el uso en bucles y que no desbordarán la pila.  
  
 Si la clase intenta asignar memoria en el montón y se produce un error, llamará a `AtlThrow` con un argumento de E_OUTOFMEMORY.  
  
 De forma predeterminada, las macros y clases de conversión de ATL usan la página de códigos ANSI del subproceso actual para la conversión. Si desea invalidar este comportamiento para una conversión concreta, especifique la página de códigos como el segundo parámetro al constructor para la clase.  
  
 Las macros siguientes se basan en esta clase:  
  
- CT2AEX  
  
- CW2TEX  
  
- CW2CTEX  
  
- CT2CAEX  
  
 La siguiente definición de tipo se basa en esta clase:  
  
- CW2A  
  
 Para obtener una explicación de estas macros de conversión de texto, consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte [Macros de conversión de cadena de MFC y ATL](string-conversion-macros.md) para obtener un ejemplo del uso de estas macros de conversión de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlconv.h  
  
##  <a name="cw2aex"></a>  CW2AEX::CW2AEX  
 El constructor.  
  
```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *psz*  
 La cadena de texto que se va a convertir.  
  
 *nCodePage*  
 La página de códigos utilizada para realizar la conversión. Vea la descripción del parámetro de página de código para la función de Windows SDK [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) para obtener más detalles.  
  
### <a name="remarks"></a>Comentarios  
 Asigna el búfer usado en el proceso de traducción.  
  
##  <a name="dtor"></a>  CW2AEX:: ~ CW2AEX  
 Destructor.  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera el búfer asignado.  
  
##  <a name="m_psz"></a>  CW2AEX::m_psz  
 El miembro de datos que almacena la cadena de origen.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer  
 El búfer estático, utilizado para almacenar la cadena convertida.  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>  CW2AEX::operator LPSTR  
 Operador de conversión.  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la cadena de texto como un tipo LPSTR.  
  
## <a name="see-also"></a>Vea también  
 [Clase CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Clase CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Clase CA2WEX](../../atl/reference/ca2wex-class.md)   
 [Clase CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Clase CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
