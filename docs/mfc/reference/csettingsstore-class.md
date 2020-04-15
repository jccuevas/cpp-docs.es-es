---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318465"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Incluye las funciones API de Windows, proporcionando una interfaz orientada a objetos que se utiliza para tener acceso al registro.

## <a name="syntax"></a>Sintaxis

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Construye un objeto `CSettingsStore`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSettingsStore::Cerrar](#close)|Cierra la clave de registro abierta.|
|[CSettingsStore::CreateKey](#createkey)|Abre la clave especificada o la crea si no existe.|
|[CSettingsStore::DeleteKey](#deletekey)|Elimina la clave especificada y todos sus elementos secundarios.|
|[CSettingsStore::DeleteValue](#deletevalue)|Elimina el valor especificado de la clave abierta.|
|[CSettingsStore::Abrir](#open)|Abre la clave especificada.|
|[CSettingsStore::Leer](#read)|Recupera los datos de un valor de clave especificado.|
|[CSettingsStore::Escribir](#write)|Escribe un valor en el registro bajo la clave abierta.|

## <a name="remarks"></a>Observaciones

Las `CreateKey` funciones `Open` miembro y son muy similares. Si la clave del `CreateKey` Registro `Open` ya existe y funzora de la misma manera. Sin embargo, si la `CreateKey` clave del Registro `Open` no existe, la creará mientras que devolverá un valor de error.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `CSettingsStore` los métodos Open y Read de la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de información sobre herramientas.

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Cerrar

Cierra la clave de registro abierta.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, se llama a este método desde el destructor de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::CreateKey

Abre una clave del Registro o la crea si no existe.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[en] Especifica el nombre de una clave que se va a crear o abrir.

### <a name="return-value"></a>Valor devuelto

0 si tiene éxito; de lo contrario un valor distinto de cero.

### <a name="remarks"></a>Observaciones

`CreateKey`usos `m_hKey` como raíz de las consultas del registro. Busca *pszPath* como una subclave `m_hKey`de . Si la clave no `CreateKey` existe, la crea. De lo contrario, se abre la clave. `CreateKey`a `m_hKey` continuación, se establece en la clave creada o abierta.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore

Crea un objeto `CSettngsStore` .

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parámetros

*bAdmin*<br/>
[en] Parámetro booleano que `CSettingsStore` especifica si el objeto actúa en modo de administrador.

*bReadOnly*<br/>
[en] Parámetro booleano que `CSettingsStore` especifica si el objeto se crea en modo de solo lectura.

### <a name="remarks"></a>Observaciones

Si *bAdmin* se establece `m_hKey` en TRUE, la variable miembro se establece en **HKEY_LOCAL_MACHINE**. Si establece *bAdmin* en `m_hKey` FALSE, se establece **en HKEY_CURRENT_USER**.

El acceso de seguridad depende del parámetro *bReadOnly.* Si *bReadonly* es FALSE, el acceso de seguridad se establecerá en **KEY_ALL_ACCESS**. Si *bReadyOnly* es TRUE, el acceso de seguridad se establecerá en una combinación de **KEY_QUERY_VALUE, KEY_NOTIFY** y **KEY_ENUMERATE_SUB_KEYS**. Para obtener más información sobre el acceso a la seguridad junto con el registro, vea Derechos de acceso y seguridad de [claves del registro](/windows/win32/SysInfo/registry-key-security-and-access-rights).

El destructor `CSettingsStore` `m_hKey` para las versiones automáticamente.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey

Elimina una clave y todos sus elementos secundarios del registro.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[en] El nombre de la clave que se desea eliminar.

*bAdmin*<br/>
[en] Conmutador que especifica la ubicación de la clave que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Este método producirá `CSettingsStore` un error si el objeto está en modo de solo lectura.

Si el parámetro *bAdmin* es cero, `DeleteKey` busca la clave que se va a eliminar en **HKEY_CURRENT_USER**. Si *bAdmin* es `DeleteKey` distinto de cero, busca la clave que se va a eliminar en **HKEY_LOCAL_MACHINE**.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue

Elimina un valor `m_hKey`de .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parámetros

*pszValue*<br/>
[en] Especifica el campo de valor que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Abrir

Abre una clave del Registro.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[en] El nombre de una clave del Registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Después de que este método abre `m_hKey` correctamente la clave especificada, se establece en el identificador de esta clave.

## <a name="csettingsstoreread"></a><a name="read"></a>CSettingsStore::Leer

Lee un valor de una clave en el registro.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>Parámetros

*pszKey*<br/>
[en] Puntero a una cadena terminada en null que contiene el nombre del valor que se va a leer del registro.

*iVal*<br/>
[fuera] Referencia a una variable entera que recibe el valor leído de la clave del Registro.

*dwVal*<br/>
[fuera] Referencia a una variable de palabra doble de 32 bits que recibe el valor leído de la clave del Registro.

*sVal*<br/>
[fuera] Referencia a una variable de cadena que recibe el valor leído de la clave del Registro.

*scStringList*<br/>
[fuera] Referencia a una variable de lista de cadenas que recibe el valor leído de la clave del Registro.

*scArray*<br/>
[fuera] Referencia a una variable de matriz de cadenas que recibe el valor leído de la clave del Registro.

*dwcArray*<br/>
[fuera] Referencia a una variable de matriz de palabras dobles de 32 bits que recibe el valor leído de la clave del Registro.

*wcArray*<br/>
[fuera] Referencia a una variable de matriz de palabras de 16 bits que recibe el valor leído de la clave del Registro.

*bcArray*<br/>
[fuera] Referencia a una variable de matriz de bytes que recibe el valor leído de la clave del Registro.

*lpPoint*<br/>
[fuera] Referencia a un `POINT` puntero a una estructura que recibe el valor leído de la clave del Registro.

*Rect*<br/>
[fuera] Referencia a una variable [CRect](../../atl-mfc-shared/reference/crect-class.md) que recibe el valor leído de la clave del Registro.

*ppData*<br/>
[fuera] Puntero a un puntero a datos que recibe el valor leído de la clave del Registro.

*pBytes*<br/>
[fuera] Puntero a una variable de entero sin signo. Esta variable recibe el tamaño del búfer al que *apunta ppData.*

*list*<br/>
[fuera] Referencia a una variable [CObList](../../mfc/reference/coblist-class.md) que recibe el valor leído de la clave del Registro.

*obj*<br/>
[fuera] Referencia a una variable [CObject](../../mfc/reference/cobject-class.md) que recibe el valor leído de la clave del Registro.

*pObj*<br/>
[fuera] Referencia a un `CObject` puntero a una variable que recibe el valor leído de la clave del Registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

`Read`comprueba *pszKey* como una subclave de `m_hKey`.

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Escribir

Escribe un valor en el registro bajo la clave abierta.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>Parámetros

*pszKey*<br/>
[en] Puntero a una cadena que contiene el nombre del valor que se va a establecer.

*iVal*<br/>
[en] Referencia a una variable entera que contiene los datos que se almacenarán.

*dwVal*<br/>
[en] Referencia a una variable de palabra doble de 32 bits que contiene los datos que se almacenarán.

*pszVal*<br/>
[en] Puntero a una variable de cadena terminada en null que contiene los datos que se va a almacenar.

*scStringList*<br/>
[en] Referencia a una variable [CStringList](../../mfc/reference/cstringlist-class.md) que contiene los datos que se va a almacenar.

*bcArray*<br/>
[en] Referencia a una variable de matriz de bytes que contiene los datos que se almacenarán.

*scArray*<br/>
[en] Referencia a una variable de matriz de cadenas que contiene los datos que se va a almacenar.

*dwcArray*<br/>
[en] Referencia a una variable de matriz de palabras dobles de 32 bits que contiene los datos que se almacenarán.

*wcArray*<br/>
[en] Referencia a una variable de matriz de palabras de 16 bits que contiene los datos que se almacenarán.

*Rect*<br/>
[en] Referencia a una variable [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene los datos que se almacenarán.

*lpPoint*<br/>
[en] Referencia a un `POINT` puntero a una variable que contiene los datos que se almacenarán.

*pData*<br/>
[en] Puntero a un búfer que contiene los datos que se va a almacenar.

*nBytes*<br/>
[en] Especifica el tamaño, en bytes, de los datos a los que apunta el parámetro *pData.*

*list*<br/>
[en] Referencia a una variable [CObList](../../mfc/reference/coblist-class.md) que contiene los datos que se almacenarán.

*obj*<br/>
[en] Referencia a una variable [CObject](../../mfc/reference/cobject-class.md) que contiene los datos que se va a almacenar.

*pObj*<br/>
[en] Puntero a un `CObject` puntero a una variable que contiene los datos que se almacenarán.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Para escribir en el registro, debe establecer *bReadOnly* en un valor distinto de cero al crear un [CSettingsStore](../../mfc/reference/csettingsstore-class.md) objeto. Para obtener más información, vea [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)
