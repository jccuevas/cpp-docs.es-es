---
title: Clase CComVariant
ms.date: 11/04/2016
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
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496858"
---
# <a name="ccomvariant-class"></a>Clase CComVariant

Esta clase ajusta el tipo de variante, proporcionando un miembro que indica el tipo de datos almacenados.

## <a name="syntax"></a>Sintaxis

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|El constructor.|
|[CComVariant::~CComVariant](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Adjunta una variante al `CComVariant` objeto.|
|[CComVariant::ChangeType](#changetype)|Convierte el `CComVariant` objeto en un nuevo tipo.|
|[CComVariant::Clear](#clear)|Borra el `CComVariant` objeto.|
|[CComVariant::Copy](#copy)|Copia una variante en el `CComVariant` objeto.|
|[CComVariant::CopyTo](#copyto)|Copia el contenido del `CComVariant` objeto.|
|[CComVariant::Detach](#detach)|Desasocia la variante subyacente del `CComVariant` objeto.|
|[CComVariant::GetSize](#getsize)|Devuelve el tamaño en número de bytes del contenido del `CComVariant` objeto.|
|[CComVariant::ReadFromStream](#readfromstream)|Carga una variante de una secuencia.|
|[CComVariant::SetByRef](#setbyref)|Inicializa el `CComVariant` objeto y establece el `vt` miembro en VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Guarda la variante subyacente en una secuencia.|

### <a name="public-operators"></a>Operadores públicos

|||
|-|-|
|[CComVariant:: Operator <](#operator_lt)|Indica si el `CComVariant` objeto es menor que la variante especificada.|
|[CComVariant:: Operator >](#operator_gt)|Indica si el `CComVariant` objeto es mayor que la variante especificada.|
|[operator !=](#operator_neq)|Indica si el `CComVariant` objeto no es igual a la variante especificada.|
|[operador =](#operator_eq)|Asigna un valor al `CComVariant` objeto.|
|[operator ==](#operator_eq_eq)|Indica si el `CComVariant` objeto es igual a la variante especificada.|

## <a name="remarks"></a>Comentarios

`CComVariant`ajusta el tipo VARIANT y VARIANTARG, que consta de una Unión y un miembro que indica el tipo de los datos almacenados en la Unión. Las variantes se suelen usar en la automatización.

`CComVariant`deriva de la variante de tipo para que se pueda usar siempre que se pueda usar una variante. Puede, por ejemplo, usar la macro V_VT para extraer el tipo de una `CComVariant` o puede tener acceso al `vt` miembro directamente tal como lo haría con una variante.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli. h

##  <a name="attach"></a>  CComVariant::Attach

Borra de forma segura el contenido actual del `CComVariant` objeto, copia el contenido de *pSrc* en este objeto y, a continuación, establece el tipo de variante de *pSrc* en VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
de Apunta a la [variante](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a adjuntar al objeto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La propiedad de los datos que contiene *pSrc* se transfiere al `CComVariant` objeto.

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

Cada constructor controla la inicialización segura del `CComVariant` objeto llamando a la `VariantInit` función de Win32 o estableciendo el valor y el tipo del objeto según los parámetros pasados.

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

*varSrc*<br/>
de Variante o que se usa para inicializar el `CComVariant` objeto. `CComVariant` El contenido de la variante de origen se copia en el destino sin conversión.

*lpszSrc*<br/>
de Cadena de caracteres que se usa para `CComVariant` inicializar el objeto. Puede pasar una cadena de caracteres anchos (Unicode) de terminación cero a la versión LPCOLESTR del constructor o una cadena ANSI a la versión LPCSTR. En cualquier caso, la cadena se convierte en un BSTR Unicode asignado `SysAllocString`mediante. El tipo del `CComVariant` objeto será VT_BSTR.

*bSrc*<br/>
de **Bool** que se usa para inicializar el `CComVariant` objeto. El argumento **bool** se convierte en un VARIANT_BOOL antes de almacenarse. El tipo del `CComVariant` objeto será VT_BOOL.

*nSrc*<br/>
de **Int**, **byte**, **Short**, **Long**, LONGLONG, ULONGLONG, unsigned **Short**, unsigned **Long**o unsigned **int** utilizado para inicializar el `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*vtSrc*<br/>
de Tipo de la variante. Cuando el primer parámetro es **int**, los tipos válidos son VT_I4 y VT_INT. Cuando el primer parámetro es **Long**, los tipos válidos son VT_I4 y VT_ERROR. Cuando el primer parámetro es **Double**, los tipos válidos son VT_R8 y VT_DATE. Cuando el primer parámetro es un **int sin signo**, los tipos válidos son VT_UI4 y VT_UINT.

*fltSrc*<br/>
de Valor de **tipo float** que se `CComVariant` usa para inicializar el objeto. El tipo del `CComVariant` objeto será VT_R4.

*dblSrc*<br/>
de **Valor Double** que se usa para `CComVariant` inicializar el objeto. El tipo del `CComVariant` objeto será VT_R8.

*cySrc*<br/>
de Que se `CComVariant` usa para inicializar el objeto. `CY` El tipo del `CComVariant` objeto será VT_CY.

*pSrc*<br/>
de El `IDispatch` puntero `IUnknown` o utilizado para inicializar `CComVariant` el objeto. `AddRef`se llamará en el puntero de interfaz. El tipo del `CComVariant` objeto será VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, el puntero SAFERRAY se usa para `CComVariant` inicializar el objeto. Una copia de la matriz SafeArray se almacena en `CComVariant` el objeto. El tipo del `CComVariant` objeto será una combinación del tipo original de SafeArray y VT_ARRAY.

*cSrc*<br/>
de **Carácter** que se usa para inicializar el `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_I1.

*bstrSrc*<br/>
de BSTR que se usa para inicializar el `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_BSTR.

### <a name="remarks"></a>Comentarios

El destructor administra la limpieza mediante una llamada a [CComVariant:: Clear](#clear).

##  <a name="dtor"></a>  CComVariant::~CComVariant

Destructor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Comentarios

Este método administra la limpieza mediante una llamada a [CComVariant:: Clear](#clear).

##  <a name="changetype"></a>  CComVariant::ChangeType

Convierte el `CComVariant` objeto en un nuevo tipo.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*vtNew*<br/>
de Nuevo tipo `CComVariant` del objeto.

*pSrc*<br/>
de Un puntero a la variante cuyo valor se convertirá al nuevo tipo. El valor predeterminado es null, lo que `CComVariant` significa que el objeto se convertirá en su lugar.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si pasa un valor para *pSrc*, `ChangeType` usará esta variante como el origen de la conversión. De lo contrario `CComVariant` , el objeto será el origen.

##  <a name="clear"></a>  CComVariant::Clear

Borra el `CComVariant` objeto llamando a la función `VariantClear` de Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El destructor llama automáticamente `Clear`a.

##  <a name="copy"></a>  CComVariant::Copy

Libera el `CComVariant` objeto y, a continuación, le asigna una copia de la variante especificada.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
de Puntero a la [variante](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="copyto"></a>  CComVariant::CopyTo

Copia el contenido del `CComVariant` objeto.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parámetros

*pstrDest*<br/>
Apunta a un BSTR que recibirá una copia del contenido del `CComVariant` objeto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El `CComVariant` objeto debe ser de tipo VT_BSTR.

##  <a name="detach"></a>  CComVariant::Detach

Desasocia la variante subyacente del `CComVariant` objeto y establece el tipo del objeto en VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parámetros

*pDest*<br/>
enuncia Devuelve el valor VARIANT subyacente del objeto.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que el contenido de la variante a la que hace referencia *pDest* se borrará automáticamente antes de que se le asigne `CComVariant` el valor y el tipo del objeto que realiza la llamada.

##  <a name="getsize"></a>  CComVariant::GetSize

Para las variantes de tamaño simple fijo, este método devuelve el **tamaño** del tipo de datos subyacente más **sizeof (VARTYPE)** .

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño en bytes del contenido actual del `CComVariant` objeto.

### <a name="remarks"></a>Comentarios

Si la variante contiene un puntero de interfaz `GetSize` , realiza `IPersistStream` consultas `IPersistStreamInit`para o. Si se realiza correctamente, el valor devuelto es el 32 bits de orden inferior del valor `GetSizeMax` devuelto por más el **tamaño** de un CLSID y **sizeof (VARTYPE)** . Si el puntero de interfaz es null `GetSize` , devuelve el **tamaño** de un CLSID más **sizeof (VARTYPE)** . Si el tamaño total es mayor que ULONG_MAX, `GetSize` devuelve **sizeof (VARTYPE)** , que indica un error.

En todos los demás casos, una variante temporal de tipo VT_BSTR se convierte a partir de la variante actual. La longitud de este BSTR se calcula como el tamaño de la longitud de la cadena más la longitud de la propia cadena más el tamaño del carácter nulo más **sizeof (VARTYPE)** . Si la variante no se puede convertir en una variante de tipo VT_BSTR, `GetSize` devuelve **sizeof (VARTYPE)** .

El tamaño devuelto por este método coincide con el número de bytes usado por [CComVariant:: WriteToStream](#writetostream) en condiciones correctas.

##  <a name="operator_eq"></a>CComVariant:: Operator =

Asigna un valor y el `CComVariant` tipo correspondiente al objeto.

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

*varSrc*<br/>
de [Variante](/windows/win32/api/oaidl/ns-oaidl-variant) o que`CComVariant` se va a asignar `CComVariant` al objeto. El contenido de la variante de origen se copia en el destino sin conversión.

*bstrSrc*<br/>
de BSTR que se va a asignar al `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_BSTR.

*lpszSrc*<br/>
de Cadena de caracteres que se va a asignar `CComVariant` al objeto. Puede pasar una cadena de caracteres anchos (Unicode) de terminación cero a la versión LPCOLESTR del operador o una cadena ANSI a la versión LPCSTR. En cualquier caso, la cadena se convierte en un BSTR Unicode asignado mediante `SysAllocString`. El tipo del `CComVariant` objeto será VT_BSTR.

*bSrc*<br/>
de **Bool** que se va a asignar al `CComVariant` objeto. El argumento **bool** se convierte en un VARIANT_BOOL antes de almacenarse. El tipo del `CComVariant` objeto será VT_BOOL.

*nSrc*<br/>
de **Int**, byte, **Short**, **Long**, LONGLONG, ULONGLONG, unsigned **Short**, unsigned **Long**o unsigned **int** que se va a asignar al `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*fltSrc*<br/>
de Valor de **tipo float** que se va `CComVariant` a asignar al objeto. El tipo del `CComVariant` objeto será VT_R4.

*dblSrc*<br/>
de **Valor Double** que se va a asignar `CComVariant` al objeto. El tipo del `CComVariant` objeto será VT_R8.

*cySrc*<br/>
de Que se va a asignar `CComVariant` al objeto. `CY` El tipo del `CComVariant` objeto será VT_CY.

*pSrc*<br/>
de Puntero `IDispatch` o `IUnknown` quesevaa`CComVariant` asignar al objeto. `AddRef`se llamará en el puntero de interfaz. El tipo del `CComVariant` objeto será VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, un puntero SafeArray que se va a `CComVariant` asignar al objeto. Una copia de la matriz SafeArray se almacena en `CComVariant` el objeto. El tipo del `CComVariant` objeto será una combinación del tipo original de SafeArray y VT_ARRAY.

*cSrc*<br/>
de Carácter que se va a asignar al `CComVariant` objeto. El tipo del `CComVariant` objeto será VT_I1.

##  <a name="operator_eq_eq"></a>CComVariant:: Operator = =

Indica si el `CComVariant` objeto es igual a la variante especificada.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve true si el valor y el tipo de *varSrc* son iguales que el valor y el tipo, respectivamente, `CComVariant` del objeto. En caso contrario, FALSE. El operador usa la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos de variante. Compara cadenas, enteros y puntos flotantes, pero no matrices o registros.

##  <a name="operator_neq"></a>CComVariant:: Operator! =

Indica si el `CComVariant` objeto no es igual a la variante especificada.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve true si el valor o el tipo de *varSrc* no es igual al valor o tipo, respectivamente, del `CComVariant` objeto. En caso contrario, FALSE. El operador usa la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos de variante. Compara cadenas, enteros y puntos flotantes, pero no matrices o registros.

##  <a name="operator_lt"></a>CComVariant:: Operator&lt;

Indica si el `CComVariant` objeto es menor que la variante especificada.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve true si el valor del `CComVariant` objeto es menor que el valor de *varSrc*. En caso contrario, FALSE. El operador usa la configuración regional predeterminada del usuario para realizar la comparación.

##  <a name="operator_gt"></a>CComVariant:: Operator&gt;

Indica si el `CComVariant` objeto es mayor que la variante especificada.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve true si el valor del `CComVariant` objeto es mayor que el valor de *varSrc*. En caso contrario, FALSE. El operador usa la configuración regional predeterminada del usuario para realizar la comparación.

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

Establece la variante subyacente en la variante contenida en la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
de Un puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`ReadToStream`requiere una llamada anterior a [WriteToStream](#writetostream).

##  <a name="setbyref"></a>  CComVariant::SetByRef

Inicializa el `CComVariant` objeto y establece el `vt` miembro en VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de variante, por ejemplo, BSTR, **int**o **Char**.

*pT*<br/>
Puntero que se usa para inicializar el `CComVariant` objeto.

### <a name="remarks"></a>Comentarios

`SetByRef`es una plantilla de función que inicializa el `CComVariant` objeto en el puntero *PT* y establece el `vt` miembro en VT_BYREF. Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

Guarda la variante subyacente en una secuencia.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
de Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en una secuencia.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
