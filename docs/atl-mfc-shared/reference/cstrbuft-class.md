---
title: Clase CStrBufT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 695c3bc4c5e03f2ff6c1865f456b1ef358e3dcf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cstrbuft-class"></a>Clase CStrBufT
Esta clase proporciona la limpieza de recursos automático para `GetBuffer` y `ReleaseBuffer` llama en una existente `CStringT` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>Parámetros  
 *TCharType*  
 El tipo de carácter de la `CStrBufT` clase. Puede ser uno de los siguientes:  
  
- `char` (para cadenas de caracteres ANSI)  
  
- `wchar_t` (para cadenas de caracteres Unicode)  
  
- **TCHAR** (para cadenas de caracteres ANSI y Unicode)  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`PCXSTR`|Un puntero a una cadena de constante.|  
|`PXSTR`|Un puntero a una cadena.|  
|`StringType`|El tipo de cadena cuyo buffer va a ser manipulados por especializaciones de esta plantilla de clase.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|El constructor para el objeto de búfer de cadena.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|Establece la longitud del búfer de caracteres del objeto string asociado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Recupera un **const** puntero al búfer de caracteres del objeto string asociado.|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|Recupera un puntero al búfer de caracteres del objeto string asociado.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|Determinar automáticamente la nueva longitud de la cadena de la versión.|  
|[CStrBufT::SET_LENGTH](#set_length)|Establecer la longitud del objeto de cadena en tiempo de GetBuffer|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se utiliza como una clase contenedora para reemplazar las llamadas a [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), o [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) y `ReleaseBuffer`.  
  
 Ha diseñado principalmente como una clase auxiliar, `CStrBufT` proporciona una manera cómoda para que un desarrollador para que funcione con el búfer de caracteres de un objeto de cadena sin preocuparse de cómo o cuándo se debe llamar a `ReleaseBuffer`. Esto es posible porque el objeto de contenedor se sale del ámbito natural en el caso de una excepción o varias rutas de código existente; haciendo que su destructor liberar el recurso de cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpstr.h  
  
##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH  
 Determinar automáticamente la nueva longitud de la cadena de la versión.  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>Comentarios  
 Determinar automáticamente la nueva longitud de la cadena de la versión. Debe ser la cadena terminada en null.  
  
##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT  
 Construye un objeto de búfer.  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El objeto de cadena asociado con el búfer. Normalmente, el desarrollador usará las definiciones de tipos predefinidos de **CStrBuf** ( **TCHAR** variante), **CStrBufA** ( `char` variante) y **CStrBufW**  ( `wchar_t` variante).  
  
 *nMinLength*  
 La longitud mínima del búfer de caracteres.  
  
 `dwFlags`  
 Determina si la longitud de la cadena se determina automáticamente. Puede ser uno de los siguientes:  
  
- **AUTO_LENGTH** longitud de cadena es automáticamente determina cuándo [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) se llama. Debe ser la cadena terminada en null. Valor predeterminado.  
  
- **SET_LENGTH** longitud de la cadena se establece cuando [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) se llama.  
  
### <a name="remarks"></a>Comentarios  
 Crea un búfer de cadena para el objeto de cadena asociado. Durante la construcción, [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) o [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) se llama.  
  
 Tenga en cuenta que el constructor de copias es `private`.  
  
##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR  
 Obtiene acceso directamente a los caracteres que se almacenan en el objeto de cadena asociado como una cadena de estilo C.  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero de carácter a los datos de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver un puntero al búfer de caracteres de un objeto de cadena. No se puede cambiar el contenido del objeto string con this (puntero).  
  
##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR  
 Obtiene acceso directamente a los caracteres que se almacenan en el objeto de cadena asociado como una cadena de estilo C.  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero de carácter a los datos de la cadena.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para devolver un puntero al búfer de caracteres de un objeto de cadena. El desarrollador puede cambiar el contenido del objeto string con this (puntero).  
  
##  <a name="pcxstr"></a>  CStrBufT::PCXSTR  
 Un puntero a una cadena de constante.  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="pxstr"></a>  CStrBufT::PXSTR  
 Un puntero a una cadena.  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="set_length"></a>  CStrBufT::SET_LENGTH  
 Establecer la longitud del objeto de cadena en `GetBuffer` tiempo.  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>Comentarios  
 Defina la longitud del objeto de cadena en tiempo de GetBuffer.  
  
 Determina si [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) se llama cuando se construye el objeto de búfer de cadena.  
  
##  <a name="setlength"></a>  CStrBufT::SetLength  
 Establece la longitud del búfer de caracteres.  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLength`  
 La nueva longitud del búfer de caracteres del objeto string.  
  
> [!NOTE]
>  Debe ser menor o igual que la longitud del búfer mínimo especificada en el constructor de `CStrBufT`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer la longitud de la cadena representada por el objeto de búfer.  
  
##  <a name="stringtype"></a>  CStrBufT::StringType  
 El tipo de cadena cuyo buffer va a ser manipulados por especializaciones de esta plantilla de clase.  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>Comentarios  
 **TCharType** es el tipo de caracteres utilizado para especializar la plantilla de clase.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


