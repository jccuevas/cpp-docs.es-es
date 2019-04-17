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
ms.openlocfilehash: 1e1373da86c1c3fea3b1ddd6ff17f0fac4f76980
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770400"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Incluye las funciones API de Windows, proporcionando una interfaz orientada a objetos que se utiliza para tener acceso al registro.

## <a name="syntax"></a>Sintaxis

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Construye un objeto `CSettingsStore`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSettingsStore::Close](#close)|Cierra la clave del registro abierta.|
|[CSettingsStore::CreateKey](#createkey)|Se abre la clave especificada o la crea si no existe.|
|[CSettingsStore::DeleteKey](#deletekey)|Elimina la clave especificada y todos sus elementos secundarios.|
|[CSettingsStore::DeleteValue](#deletevalue)|Elimina el valor especificado de la clave abierta.|
|[CSettingsStore::Open](#open)|Se abre la clave especificada.|
|[CSettingsStore::Read](#read)|Recupera los datos de un valor de clave especificado.|
|[CSettingsStore::Write](#write)|Escribe un valor en el registro bajo la clave abierta.|

## <a name="remarks"></a>Comentarios

Las funciones miembro `CreateKey` y `Open` son muy similares. Si ya existe la clave del registro, `CreateKey` y `Open` función de la misma manera. Sin embargo, si no existe la clave del registro, `CreateKey` creará, mientras que `Open` devolverá un valor de error.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar los métodos Open y lectura de la `CSettingsStore` clase. Este fragmento de código forma parte de la [ejemplo de demostración de sugerencia de la herramienta](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsettingsstore.h

##  <a name="close"></a>  CSettingsStore::Close

Cierra la clave del registro abierta.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método se llama desde el destructor de la [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).

##  <a name="createkey"></a>  CSettingsStore::CreateKey

Se abre una clave del registro o lo crea si no existe.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[in] Especifica el nombre de una clave que se creó o se abran.

### <a name="return-value"></a>Valor devuelto

0 si es correcto; en caso contrario, un valor distinto de cero.

### <a name="remarks"></a>Comentarios

`CreateKey` usa `m_hKey` como la raíz de las consultas del registro. Busca *pszPath* como subclave de `m_hKey`. Si la clave no existe, `CreateKey` lo crea. En caso contrario, abre la clave. `CreateKey` a continuación, establece `m_hKey` a la clave creada o abierta.

##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore

Crea un objeto `CSettngsStore`.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parámetros

*bAdmin*<br/>
[in] Parámetro booleano que especifica si el `CSettingsStore` objeto actúa en modo de administrador.

*bReadOnly*<br/>
[in] Parámetro booleano que especifica si el `CSettingsStore` objeto se crea en modo de solo lectura.

### <a name="remarks"></a>Comentarios

Si *bruta administrativa* está establecida en TRUE, el `m_hKey` variable de miembro se establece en **HKEY_LOCAL_MACHINE**. Si establece *bruta administrativa* en FALSE, `m_hKey` está establecido en **HKEY_CURRENT_USER**.

El acceso de seguridad depende del *bReadOnly* parámetro. Si *bReadonly* es FALSE, el acceso de seguridad se establecerá en **KEY_ALL_ACCESS**. Si *bReadyOnly* es TRUE, el acceso de seguridad se establecerá en una combinación de **KEY_QUERY_VALUE, KEY_NOTIFY** y **KEY_ENUMERATE_SUB_KEYS**. Para obtener más información acerca del acceso de seguridad junto con el registro, consulte [derechos de acceso y seguridad de la clave del registro](/windows/desktop/SysInfo/registry-key-security-and-access-rights).

El destructor de `CSettingsStore` libera `m_hKey` automáticamente.

##  <a name="deletekey"></a>  CSettingsStore::DeleteKey

Elimina una clave y todos sus elementos secundarios del registro.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[in] El nombre de la clave que se va a eliminar.

*bAdmin*<br/>
[in] Modificador que especifica la ubicación de la clave que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este método se producirá un error si el `CSettingsStore` objeto está en modo de solo lectura.

Si el parámetro *bruta administrativa* es cero, `DeleteKey` busca la clave que se va a eliminar en **HKEY_CURRENT_USER**. Si *bruta administrativa* es distinto de cero, `DeleteKey` busca la clave que se va a eliminar en **HKEY_LOCAL_MACHINE**.

##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue

Elimina un valor de `m_hKey`.

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parámetros

*pszValue*<br/>
[in] Especifica el campo de valor para quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="open"></a>  CSettingsStore::Open

Se abre una clave del registro.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
[in] El nombre de una clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Después de este método abre correctamente la clave especificada, establece `m_hKey` al identificador de esta clave.

##  <a name="read"></a>  CSettingsStore::Read

Lee un valor de una clave del registro.

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
[in] Puntero a una cadena terminada en null que contiene el nombre del valor que se va a leer del registro.

*iVal*<br/>
[out] Referencia a una variable entera que recibe el valor leído de la clave del registro.

*dwVal*<br/>
[out] Referencia a una variable de doble palabra de 32 bits que recibe el valor leído de la clave del registro.

*sVal*<br/>
[out] Referencia a una variable de cadena que recibe el valor leído de la clave del registro.

*scStringList*<br/>
[out] Referencia a una variable de la lista de cadena que recibe el valor leído de la clave del registro.

*scArray*<br/>
[out] Referencia a una variable de matriz de cadena que recibe el valor leído de la clave del registro.

*dwcArray*<br/>
[out] Referencia a una variable de matriz de doble palabra de 32 bits que recibe el valor leído de la clave del registro.

*wcArray*<br/>
[out] Referencia a una variable de matriz de palabras de 16 bits que recibe el valor leído de la clave del registro.

*bcArray*<br/>
[out] Referencia a una variable de matriz de bytes que recibe el valor leído de la clave del registro.

*lpPoint*<br/>
[out] Referencia a un puntero a un `POINT` lee de estructura que recibe el valor de la clave del registro.

*rect*<br/>
[out] Hacer referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) variable que recibe el valor leído desde la clave del registro.

*ppData*<br/>
[out] Puntero a un puntero a los datos que recibe el valor de lee la clave del registro.

*pBytes*<br/>
[out] Puntero a una variable de entero sin signo. Esta variable recibe el tamaño del búfer que *ppData* apunta a.

*lista*<br/>
[out] Hacer referencia a un [CObList](../../mfc/reference/coblist-class.md) variable que recibe el valor leído desde la clave del registro.

*obj*<br/>
[out] Hacer referencia a un [CObject](../../mfc/reference/cobject-class.md) variable que recibe el valor leído desde la clave del registro.

*pObj*<br/>
[out] Referencia a un puntero a un `CObject` variable que recibe el valor leído desde la clave del registro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

`Read` comprueba si hay *pszKey* como subclave de `m_hKey`.

##  <a name="write"></a>  CSettingsStore::Write

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
[in] Puntero a una cadena que contiene el nombre del valor que se establece.

*iVal*<br/>
[in] Referencia a una variable de entero que contiene los datos que se va a almacenar.

*dwVal*<br/>
[in] Referencia a una variable de doble palabra de 32 bits que contiene los datos que se va a almacenar.

*pszVal*<br/>
[in] Puntero a una variable de cadena terminada en null que contiene los datos que se va a almacenar.

*scStringList*<br/>
[in] Hacer referencia a un [CStringList](../../mfc/reference/cstringlist-class.md) variable que contiene los datos que se va a almacenar.

*bcArray*<br/>
[in] Referencia a una variable de matriz de bytes que contiene los datos que se va a almacenar.

*scArray*<br/>
[in] Referencia a una variable de matriz de cadena que contiene los datos que se va a almacenar.

*dwcArray*<br/>
[in] Referencia a una variable de matriz de doble palabra de 32 bits que contiene los datos que se va a almacenar.

*wcArray*<br/>
[in] Referencia a una variable de matriz de palabras de 16 bits que contiene los datos que se va a almacenar.

*rect*<br/>
[in] Hacer referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) variable que contiene los datos que se va a almacenar.

*lpPoint*<br/>
[in] Referencia a un puntero a un `POINT` variable que contiene los datos que se va a almacenar.

*pData*<br/>
[in] Puntero a un búfer que contiene los datos que se va a almacenar.

*nBytes*<br/>
[in] Especifica el tamaño, en bytes, de los datos a la que el *pData* puntos del parámetro.

*lista*<br/>
[in] Hacer referencia a un [CObList](../../mfc/reference/coblist-class.md) variable que contiene los datos que se va a almacenar.

*obj*<br/>
[in] Hacer referencia a un [CObject](../../mfc/reference/cobject-class.md) variable que contiene los datos que se va a almacenar.

*pObj*<br/>
[in] Puntero a un puntero a un `CObject` variable que contiene los datos que se va a almacenar.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para poder escribir en el registro, debe establecer *bReadOnly* en un valor distinto de cero cuando se crea un [CSettingsStore](../../mfc/reference/csettingsstore-class.md) objeto. Para obtener más información, consulte [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)
