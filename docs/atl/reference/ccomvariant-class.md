---
title: CComVariant (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf9fbd4967bbd3091d734f9b70aed9350d63a25e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753199"
---
# <a name="ccomvariant-class"></a>CComVariant (clase)

Esta clase encapsula el tipo de variante, que proporciona a un miembro que indica el tipo de datos almacenados.

## <a name="syntax"></a>Sintaxis

```  
cpp
class CComVariant : public tagVARIANT  
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|El constructor.|
|[CComVariant:: ~ CComVariant](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Adjunta una variante para la `CComVariant` objeto.|
|[CComVariant::ChangeType](#changetype)|Convierte el `CComVariant` objeto a un nuevo tipo.|
|[CComVariant::Clear](#clear)|Borra la `CComVariant` objeto.|
|[CComVariant::Copy](#copy)|Copia una variante para la `CComVariant` objeto.|
|[CComVariant::CopyTo](#copyto)|Copia el contenido de la `CComVariant` objeto.|
|[CComVariant::Detach](#detach)|Desasocia la variante subyacente desde la `CComVariant` objeto.|
|[CComVariant::GetSize](#getsize)|Devuelve el tamaño en el número de bytes del contenido de la `CComVariant` objeto.|
|[CComVariant::ReadFromStream](#readfromstream)|Carga una variante de una secuencia.|
|[CComVariant::SetByRef](#setbyref)|Inicializa el `CComVariant` objeto y establece el `vt` miembro VT_BYREF.|
|[CComVariant:: WriteToStream](#writetostream)|Guarda la variante subyacente en una secuencia.|

### <a name="public-operators"></a>Operadores públicos

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Indica si el `CComVariant` objeto es menor que la variante especificada.|
|[CComVariant::operator >](#operator_gt)|Indica si el `CComVariant` objeto es mayor que la variante especificada.|
|[operator !=](#operator_neq)|Indica si el `CComVariant` objeto no es igual a la variante especificada.|
|[operador =](#operator_eq)|Asigna un valor a la `CComVariant` objeto.|
|[operator ==](#operator_eq_eq)|Indica si el `CComVariant` objeto es igual a la variante especificada.|

## <a name="remarks"></a>Comentarios

`CComVariant` ajusta el tipo VARIANT y VARIANTARG, que consta de una unión y un miembro que indica el tipo de los datos almacenados en la unión. Las variantes se utilizan normalmente en Automation.

`CComVariant` deriva el tipo de variante para que pueda usar siempre que se puede usar una variante. Por ejemplo, puede utilizar la macro V_VT para extraer el tipo de un `CComVariant` o puede tener acceso el `vt` directamente solo se puede hacer con una variante del miembro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

##  <a name="attach"></a>  CComVariant::Attach

Borra el contenido actual de forma segura la `CComVariant` de objetos, copia el contenido de *pSrc* en este objeto, a continuación, Establece el tipo de variante de *pSrc* en VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*  
[in] Apunta a la [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) para adjuntarlo al objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La propiedad de los datos mantenidos en *pSrc* se transfiere a la `CComVariant` objeto.

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

Cada constructor controla la inicialización segura de la `CComVariant` objeto mediante una llamada a la `VariantInit` función Win32 o estableciendo el valor del objeto y el tipo según los parámetros pasados.

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*  
[in] El `CComVariant` o variante que se usa para inicializar el `CComVariant` objeto. El contenido de la variante de origen se copia en el destino sin conversión.

*lpszSrc*  
[in] La cadena de caracteres utilizada para inicializar el `CComVariant` objeto. Puede pasar una cadena de caracteres terminada en cero ancha (Unicode) a la versión LPCOLESTR del constructor o una cadena ANSI para la versión LPCSTR. En cualquier caso, la cadena se convierte en un BSTR asignado mediante Unicode `SysAllocString`. El tipo de la `CComVariant` objeto será VT_BSTR.

*bSrc*  
[in] El **bool** utilizado para inicializar el `CComVariant` objeto. El **bool** argumento se convierte en un VARIANT_BOOL antes de almacenarse. El tipo de la `CComVariant` objeto será VT_BOOL.

*nSrc*  
[in] El **int**, **bytes**, **corto**, **largo**, LONGLONG, ULONGLONG, **entero corto sin signo**, **unsigned long**, o **int sin signo** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*vtSrc*  
[in] El tipo de la variante. Cuando el primer parámetro es **int**, los tipos válidos son VT_I4 y VT_INT. Cuando el primer parámetro es **largo**, los tipos válidos son VT_I4 y VT_ERROR. Cuando el primer parámetro es **doble**, los tipos válidos son VT_R8 y VT_DATE. Cuando el primer parámetro es **int sin signo**, los tipos válidos son VT_UI4 y VT_UINT.

*fltSrc*  
[in] El **float** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_R4.

*dblSrc*  
[in] El **doble** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_R8.

*cySrc*  
[in] El `CY` utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_CY.

*pSrc*  
[in] El `IDispatch` o `IUnknown` puntero usado para inicializar el `CComVariant` objeto. `AddRef` se llamará en el puntero de interfaz. El tipo de la `CComVariant` objeto será VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, el puntero SAFERRAY utilizado para inicializar el `CComVariant` objeto. Una copia de una matriz SAFEARRAY se almacena en la `CComVariant` objeto. El tipo de la `CComVariant` objeto será una combinación del tipo original de la matriz SAFEARRAY y VT_ARRAY.

*cSrc*  
[in] El **char** utilizado para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_I1.

*bstrSrc*  
[in] BSTR que se usa para inicializar el `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_BSTR.

### <a name="remarks"></a>Comentarios

El destructor administra la limpieza mediante una llamada a [CComVariant::Clear](#clear).

##  <a name="dtor"></a>  CComVariant:: ~ CComVariant

Destructor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Comentarios

Este método administra la limpieza mediante una llamada a [CComVariant::Clear](#clear).

##  <a name="changetype"></a>  CComVariant::ChangeType

Convierte el `CComVariant` objeto a un nuevo tipo.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*vtNew*  
[in] El nuevo tipo para el `CComVariant` objeto.

*pSrc*  
[in] Un puntero a la variante cuyo valor se convertirá en el nuevo tipo. El valor predeterminado es NULL, significado el `CComVariant` objeto se convertirá en su lugar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si se pasa un valor para *pSrc*, `ChangeType` esta variante se usará como origen para la conversión. En caso contrario, el `CComVariant` objeto será el origen.

##  <a name="clear"></a>  CComVariant::Clear

Borra la `CComVariant` objeto mediante una llamada a la `VariantClear` función de Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El destructor llama automáticamente a `Clear`.

##  <a name="copy"></a>  CComVariant::Copy

Libera el `CComVariant` de objeto y, a continuación, le asigna una copia de la variante especificada.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*  
[in] Un puntero a la [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) va a copiar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="copyto"></a>  CComVariant::CopyTo

Copia el contenido de la `CComVariant` objeto.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parámetros

*pstrDest*  
Apunta a un valor BSTR que recibirá una copia del contenido de la `CComVariant` objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La `CComVariant` objeto debe ser de tipo VT_BSTR.

##  <a name="detach"></a>  CComVariant::Detach

Desasocia la variante subyacente desde la `CComVariant` objeto y establece el tipo del objeto en VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parámetros

*pDest*  
[out] Devuelve el valor de variante subyacente del objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que el contenido de la variante al que hace referencia *pDest* se borrará automáticamente antes de que se asigna el valor y tipo de la llamada a `CComVariant` objeto.

##  <a name="getsize"></a>  CComVariant::GetSize

Para las variantes de tamaño fijo en simple, este método devuelve el **sizeof** el tipo de datos subyacente más **sizeof(VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño en bytes del contenido actual de la `CComVariant` objeto.

### <a name="remarks"></a>Comentarios

Si la variante contiene un puntero de interfaz `GetSize` consulta `IPersistStream` o `IPersistStreamInit`. Si es correcto, el valor devuelto es los 32 bits de orden inferior del valor devuelto por `GetSizeMax` más el **sizeof** CLSID y **sizeof(VARTYPE)**. Si el puntero de interfaz es NULL, `GetSize` devuelve el **sizeof** CLSID más **sizeof(VARTYPE)**. Si el tamaño total es mayor que ULONG_MAX, `GetSize` devuelve **sizeof(VARTYPE)** que indica un error.

En todos los demás casos, se convierte una variante de tipo VT_BSTR temporal de la variante actual. La longitud de este BSTR se calcula como el tamaño de la longitud de la cadena y la longitud de la propia cadena más el tamaño del carácter nulo más **sizeof(VARTYPE)**. Si la variante no se puede convertir en un tipo VARIANT de tipo VT_BSTR, `GetSize` devuelve **sizeof(VARTYPE)**.

El tamaño devuelto por este método coincide con el número de bytes usados por [CComVariant:: WriteToStream](#writetostream) bajo las condiciones correctas.

##  <a name="operator_eq"></a>  CComVariant::operator =

Asigna un valor y el tipo correspondiente a la `CComVariant` objeto.

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>Parámetros

*varSrc*  
[in] El `CComVariant` o [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) que se asignará a la `CComVariant` objeto. El contenido de la variante de origen se copia en el destino sin conversión.

*bstrSrc*  
[in] BSTR que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_BSTR.

*lpszSrc*  
[in] La cadena de caracteres que se asignará a la `CComVariant` objeto. Puede pasar una cadena de caracteres terminada en cero ancha (Unicode) a la versión LPCOLESTR del operador o una cadena ANSI para la versión LPCSTR. En cualquier caso, la cadena se convierte en un BSTR asignado mediante Unicode `SysAllocString`. El tipo de la `CComVariant` objeto será VT_BSTR.

*bSrc*  
[in] El **bool** que se asignará a la `CComVariant` objeto. El **bool** argumento se convierte en un VARIANT_BOOL antes de almacenarse. El tipo de la `CComVariant` objeto será VT_BOOL.

*nSrc*  
[in] El **int**, BYTE, **corto**, **largo**, LONGLONG, ULONGLONG, **entero corto sin signo**, **unsigned long**, o **int sin signo** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*fltSrc*  
[in] El **float** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_R4.

*dblSrc*  
[in] El **doble** que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_R8.

*cySrc*  
[in] El `CY` que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_CY.

*pSrc*  
[in] El `IDispatch` o `IUnknown` puntero que se asignará a la `CComVariant` objeto. `AddRef` se llamará en el puntero de interfaz. El tipo de la `CComVariant` objeto será VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, un puntero SAFEARRAY que se asignará a la `CComVariant` objeto. Una copia de una matriz SAFEARRAY se almacena en la `CComVariant` objeto. El tipo de la `CComVariant` objeto será una combinación del tipo original de la matriz SAFEARRAY y VT_ARRAY.

*cSrc*  
[in] El carácter que se asignará a la `CComVariant` objeto. El tipo de la `CComVariant` objeto será VT_I1.

##  <a name="operator_eq_eq"></a>  CComVariant::operator ==

Indica si el `CComVariant` objeto es igual a la variante especificada.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el valor y tipo de *varSrc* son iguales que el valor y tipo, respectivamente, de la `CComVariant` objeto. En caso contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos variantes. Compara cadenas, enteros y puntos flotantes, pero no las matrices o registros.

##  <a name="operator_neq"></a>  CComVariant::operator! =

Indica si el `CComVariant` objeto no es igual a la variante especificada.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el valor o el tipo de *varSrc* no es igual al valor o tipo, respectivamente, de la `CComVariant` objeto. En caso contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos variantes. Compara cadenas, enteros y puntos flotantes, pero no las matrices o registros.

##  <a name="operator_lt"></a>  CComVariant::operator &lt;

Indica si el `CComVariant` objeto es menor que la variante especificada.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el valor de la `CComVariant` objeto es menor que el valor de *varSrc*. En caso contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

##  <a name="operator_gt"></a>  CComVariant::operator &gt;

Indica si el `CComVariant` objeto es mayor que la variante especificada.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve TRUE si el valor de la `CComVariant` objeto es mayor que el valor de *varSrc*. En caso contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

Establece la variante subyacente a la variante que contiene la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*  
[in] Un puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`ReadToStream` requiere una llamada anterior a [WriteToStream](#writetostream).

##  <a name="setbyref"></a>  CComVariant::SetByRef

Inicializa el `CComVariant` objeto y establece el `vt` miembro VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parámetros

*T*  
El tipo de variante, por ejemplo, BSTR, **int**, o **char**.

*pT*  
El puntero que se usa para inicializar el `CComVariant` objeto.

### <a name="remarks"></a>Comentarios

`SetByRef` es una plantilla de función que inicializa el `CComVariant` objeto en el puntero *pT* y establece el `vt` miembro VT_BYREF. Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant:: WriteToStream

Guarda la variante subyacente en una secuencia.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*  
[in] Un puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz en una secuencia.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)