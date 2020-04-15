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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327227"
---
# <a name="ccomvariant-class"></a>Clase CComVariant

Esta clase ajusta el tipo VARIANT, proporcionando un miembro que indica el tipo de datos almacenados.

## <a name="syntax"></a>Sintaxis

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComvariant::CComvariant](#ccomvariant)|El constructor.|
|[CComvariant::-CComvariant](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComVariant::Attach](#attach)|Asocia un VARIANT `CComVariant` al objeto.|
|[CComVariant::ChangeType](#changetype)|Convierte el `CComVariant` objeto en un nuevo tipo.|
|[CComvariant::Clear](#clear)|Borra el `CComVariant` objeto.|
|[CComVariant::Copy](#copy)|Copia un VARIANT `CComVariant` en el objeto.|
|[CComvariant::CopyTo](#copyto)|Copia el contenido `CComVariant` del objeto.|
|[CComVariant::Detach](#detach)|Separa el VARIANT subyacente `CComVariant` del objeto.|
|[CComvariant::GetSize](#getsize)|Devuelve el tamaño en número de `CComVariant` bytes del contenido del objeto.|
|[CComvariant::ReadFromStream](#readfromstream)|Carga un VARIANT desde una secuencia.|
|[CComvariant::SetByRef](#setbyref)|Inicializa el `CComVariant` objeto y `vt` establece el miembro en VT_BYREF.|
|[CComvariant::WriteTostream](#writetostream)|Guarda el VARIANT subyacente en una secuencia.|

### <a name="public-operators"></a>Operadores públicos

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Indica si `CComVariant` el objeto es menor que el VARIANT especificado.|
|[CComVariant::operator >](#operator_gt)|Indica si `CComVariant` el objeto es mayor que el VARIANT especificado.|
|[operador !-](#operator_neq)|Indica si `CComVariant` el objeto no es igual al VARIANT especificado.|
|[operador a la operadora de la red](#operator_eq)|Asigna un valor `CComVariant` al objeto.|
|[operador ?](#operator_eq_eq)|Indica si `CComVariant` el objeto es igual al VARIANT especificado.|

## <a name="remarks"></a>Observaciones

`CComVariant`ajusta el tipo VARIANT y VARIANTARG, que consta de una unión y un miembro que indica el tipo de los datos almacenados en la unión. LOS VARIANTs se utilizan normalmente en Automation.

`CComVariant`deriva del tipo VARIANT para que se pueda utilizar dondequiera que se pueda utilizar un VARIANT. Por ejemplo, puede utilizar la macro V_VT para `CComVariant` extraer el `vt` tipo de a o puede acceder al miembro directamente del mismo modo que puede hacerlo con un VARIANT.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CComVariant::Attach

Borra de forma segura `CComVariant` el contenido actual del objeto, copia el contenido de *pSrc* en este objeto y, a continuación, establece el tipo de variante de *pSrc* en VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
[en] Apunta al [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a adjuntar al objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La propiedad de los datos en poder `CComVariant` de *pSrc* se transfiere al objeto.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CComvariant::CComvariant

Cada constructor controla la `CComVariant` inicialización `VariantInit` segura del objeto llamando a la función Win32 o estableciendo el valor y el tipo del objeto según los parámetros pasados.

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
[en] El `CComVariant` o VARIANT utilizado `CComVariant` para inicializar el objeto. El contenido de la variante de origen se copia en el destino sin conversión.

*lpszSrc*<br/>
[en] Cadena de caracteres `CComVariant` utilizada para inicializar el objeto. Puede pasar una cadena de caracteres anchos (Unicode) terminada en cero a la versión LPCOLESTR del constructor o una cadena ANSI a la versión LPCSTR. En cualquier caso, la cadena se convierte `SysAllocString`en un BSTR Unicode asignado mediante . El tipo `CComVariant` del objeto se VT_BSTR.

*bSrc*<br/>
[en] El **bool** utilizado `CComVariant` para inicializar el objeto. El argumento **bool** se convierte en un VARIANT_BOOL antes de almacenarse. El tipo `CComVariant` del objeto se VT_BOOL.

*nSrc*<br/>
[en] El **int**, **BYTE**, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**o **unsigned int** usado para inicializar el `CComVariant` objeto. El tipo `CComVariant` del objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*vtSrc*<br/>
[en] El tipo de la variante. Cuando el primer parámetro es **int**, los tipos válidos se VT_I4 y VT_INT. Cuando el primer parámetro es **largo,** los tipos válidos se VT_I4 y VT_ERROR. Cuando el primer parámetro es **double**, los tipos válidos se VT_R8 y VT_DATE. Cuando el primer parámetro es **unsigned int**, los tipos válidos se VT_UI4 y VT_UINT.

*fltSrc*<br/>
[en] El **float** utilizado `CComVariant` para inicializar el objeto. El tipo `CComVariant` del objeto se VT_R4.

*dblSrc*<br/>
[en] El **doble** utilizado `CComVariant` para inicializar el objeto. El tipo `CComVariant` del objeto se VT_R8.

*cySrc*<br/>
[en] Se `CY` utiliza para `CComVariant` inicializar el objeto. El tipo `CComVariant` del objeto se VT_CY.

*pSrc*<br/>
[en] El `IDispatch` `IUnknown` puntero o se `CComVariant` utiliza para inicializar el objeto. `AddRef`se llamará en el puntero de la interfaz. El tipo `CComVariant` del objeto se VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, el puntero SAFERRAY utilizado para inicializar el `CComVariant` objeto. Una copia de SAFEARRAY se `CComVariant` almacena en el objeto. El tipo `CComVariant` del objeto será una combinación del tipo original de SAFEARRAY y VT_ARRAY.

*Csrc*<br/>
[en] El **char** utilizado `CComVariant` para inicializar el objeto. El tipo `CComVariant` del objeto se VT_I1.

*bstrSrc*<br/>
[en] El BSTR utilizado `CComVariant` para inicializar el objeto. El tipo `CComVariant` del objeto se VT_BSTR.

### <a name="remarks"></a>Observaciones

El destructor administra la limpieza llamando a [CComVariant::Clear](#clear).

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CComvariant::-CComvariant

Destructor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Observaciones

Este método administra la limpieza mediante una llamada a [CComVariant::Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CComVariant::ChangeType

Convierte el `CComVariant` objeto en un nuevo tipo.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*vtNew*<br/>
[en] El nuevo tipo `CComVariant` para el objeto.

*pSrc*<br/>
[en] Puntero a VARIANT cuyo valor se convertirá al nuevo tipo. El valor predeterminado es `CComVariant` NULL, lo que significa que el objeto se convertirá en su lugar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si pasa un valor para `ChangeType` *pSrc*, utilizará este VARIANT como origen para la conversión. De lo `CComVariant` contrario, el objeto será el origen.

## <a name="ccomvariantclear"></a><a name="clear"></a>CComvariant::Clear

Borra el `CComVariant` objeto llamando `VariantClear` a la función Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El destructor `Clear`llama automáticamente a .

## <a name="ccomvariantcopy"></a><a name="copy"></a>CComVariant::Copy

Libera el `CComVariant` objeto y, a continuación, le asigna una copia del VARIANT especificado.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
[en] Un puntero a la [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CComvariant::CopyTo

Copia el contenido `CComVariant` del objeto.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parámetros

*pstrDest*<br/>
Señala a un BSTR que recibirá una `CComVariant` copia del contenido del objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El `CComVariant` objeto debe ser de tipo VT_BSTR.

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

Separa el VARIANT subyacente `CComVariant` del objeto y establece el tipo del objeto en VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parámetros

*pDest*<br/>
[fuera] Devuelve el valor VARIANT subyacente del objeto.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que el contenido de la VARIANT a la que hace referencia `CComVariant` *pDest* se borrará automáticamente antes de que se le asigne el valor y el tipo del objeto de llamada.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CComvariant::GetSize

Para VARIANTs de tamaño fijo simple, este método devuelve el **tamaño del** tipo de datos subyacente más **sizeof(VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño en bytes del `CComVariant` contenido actual del objeto.

### <a name="remarks"></a>Observaciones

Si el VARIANT contiene `GetSize` un puntero `IPersistStream` `IPersistStreamInit`de interfaz, consulta o . Si se realiza correctamente, el valor devuelto es el `GetSizeMax` orden bajo de 32 bits del valor devuelto por más el **tamaño de** un CLSID y **sizeof(VARTYPE)**. Si el puntero de `GetSize` interfaz es NULL, devuelve el **sizeof** un CLSID más **sizeof(VARTYPE)**. Si el tamaño total es `GetSize` mayor que ULONG_MAX, devuelve **sizeof(VARTYPE)** que indica un error.

En todos los demás casos, un VARIANT temporal de tipo VT_BSTR se coacciona a partir de la VARIANT actual. La longitud de este BSTR se calcula como el tamaño de la longitud de la cadena más la longitud de la propia cadena más el tamaño del carácter nulo más **sizeof(VARTYPE)**. Si el VARIANT no se puede coaccionar `GetSize` a un VARIANT de tipo VT_BSTR, devuelve **sizeof(VARTYPE)**.

El tamaño devuelto por este método coincide con el número de bytes utilizados por [CComVariant::WriteToStream](#writetostream) en condiciones correctas.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::operador ?

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
[en] El `CComVariant` o [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) que `CComVariant` se va a asignar al objeto. El contenido de la variante de origen se copia en el destino sin conversión.

*bstrSrc*<br/>
[en] El BSTR que se `CComVariant` asignará al objeto. El tipo `CComVariant` del objeto se VT_BSTR.

*lpszSrc*<br/>
[en] Cadena de caracteres que `CComVariant` se asignará al objeto. Puede pasar una cadena de caracteres anchos (Unicode) de terminación cero a la versión LPCOLESTR del operador o una cadena ANSI a la versión LPCSTR. En cualquier caso, la cadena se convierte en `SysAllocString`un BSTR Unicode asignado mediante . El tipo `CComVariant` del objeto se VT_BSTR.

*bSrc*<br/>
[en] El **bool** que se `CComVariant` asignará al objeto. El argumento **bool** se convierte en un VARIANT_BOOL antes de almacenarse. El tipo `CComVariant` del objeto se VT_BOOL.

*nSrc*<br/>
[en] El **int**, BYTE, **short**, **long**, LONGLONG, ULONGLONG, **unsigned short**, **unsigned long**o **unsigned int** que se va a asignar al `CComVariant` objeto. El tipo `CComVariant` del objeto será VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 o VT_UI4, respectivamente.

*fltSrc*<br/>
[en] El **float** que se `CComVariant` asignará al objeto. El tipo `CComVariant` del objeto se VT_R4.

*dblSrc*<br/>
[en] El **doble** que se `CComVariant` asignará al objeto. El tipo `CComVariant` del objeto se VT_R8.

*cySrc*<br/>
[en] El `CY` que se `CComVariant` asignará al objeto. El tipo `CComVariant` del objeto se VT_CY.

*pSrc*<br/>
[en] El `IDispatch` `IUnknown` puntero o puntero `CComVariant` que se va a asignar al objeto. `AddRef`se llamará en el puntero de la interfaz. El tipo `CComVariant` del objeto se VT_DISPATCH o VT_UNKNOWN, respectivamente.

O bien, un puntero SAFEARRAY `CComVariant` que se asignará al objeto. Una copia de SAFEARRAY se `CComVariant` almacena en el objeto. El tipo `CComVariant` del objeto será una combinación del tipo original de SAFEARRAY y VT_ARRAY.

*Csrc*<br/>
[en] El char que se `CComVariant` asignará al objeto. El tipo `CComVariant` del objeto se VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::operador ?

Indica si `CComVariant` el objeto es igual al VARIANT especificado.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el valor y el tipo de *varSrc* son `CComVariant` iguales al valor y tipo, respectivamente, del objeto. De lo contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos de variante. Compara cadenas, enteros y puntos flotantes, pero no matrices o registros.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::operador !o

Indica si `CComVariant` el objeto no es igual al VARIANT especificado.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el valor o tipo de *varSrc* no es igual `CComVariant` al valor o tipo, respectivamente, del objeto. De lo contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

El operador compara solo el valor de los tipos de variante. Compara cadenas, enteros y puntos flotantes, pero no matrices o registros.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant::operator&lt;

Indica si `CComVariant` el objeto es menor que el VARIANT especificado.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el `CComVariant` valor del objeto es menor que el valor de *varSrc*. De lo contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant::operator&gt;

Indica si `CComVariant` el objeto es mayor que el VARIANT especificado.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve TRUE si el `CComVariant` valor del objeto es mayor que el valor de *varSrc*. De lo contrario, FALSE. El operador utiliza la configuración regional predeterminada del usuario para realizar la comparación.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CComvariant::ReadFromStream

Establece el VARIANT subyacente en el VARIANT contenido en la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`ReadToStream`requiere una llamada anterior a [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CComvariant::SetByRef

Inicializa el `CComVariant` objeto y `vt` establece el miembro en VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de VARIANT, por ejemplo, BSTR, **int**o **char**.

*Pt*<br/>
El puntero utilizado `CComVariant` para inicializar el objeto.

### <a name="remarks"></a>Observaciones

`SetByRef`es una plantilla de `CComVariant` función que inicializa el `vt` objeto en el puntero *pT* y establece el miembro en VT_BYREF. Por ejemplo:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CComvariant::WriteTostream

Guarda el VARIANT subyacente en una secuencia.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Un puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en una secuencia.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
