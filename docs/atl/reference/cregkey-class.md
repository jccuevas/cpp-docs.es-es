---
title: Clase CRegKey
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: d3bdb2e7c3ab0ef56ef7f6fba5d43f1ba0bb7fc6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746509"
---
# <a name="cregkey-class"></a>Clase CRegKey

Esta clase proporciona métodos para manipular entradas en el registro del sistema.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CRegKey
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|El constructor.|
|[CRegKey::-CRegKey](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRegKey::Attach](#attach)|Llame a este método para `CRegKey` asociar un HKEY al `hKey`objeto estableciendo el [m_hKey](#m_hkey) identificador de miembro en .|
|[CRegKey::Cerrar](#close)|Llame a este método para liberar el identificador de miembro [m_hKey](#m_hkey) y establecerlo en NULL.|
|[CRegKey::Create](#create)|Llame a este método para crear la clave especificada, si `hKeyParent`no existe como una subclave de .|
|[CRegKey::DeleteSubKey](#deletesubkey)|Llame a este método para quitar la clave especificada del registro.|
|[CRegKey::DeleteValue](#deletevalue)|Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Llame a este método para separar `CRegKey` el identificador `m_hKey` de miembro [m_hKey](#m_hkey) del objeto y establecerlo en NULL.|
|[CRegKey::EnumKey](#enumkey)|Llame a este método para enumerar las subclaves de la clave de registro abierta.|
|[CRegKey::Flush](#flush)|Llame a este método para escribir todos los atributos de la clave de registro abierta en el registro.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave de registro abierta.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Este método notifica al autor de la llamada acerca de los cambios en los atributos o el contenido de la clave de registro abierta.|
|[CRegKey::Open](#open)|Llame a este método para abrir la clave especificada y establecer [m_hKey](#m_hkey) en el identificador de esta clave.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Llame a este método para recuperar los datos binarios para un nombre de valor especificado.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Llame a este método para recuperar los datos DWORD para un nombre de valor especificado.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Llame a este método para recuperar los datos GUID para un nombre de valor especificado.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Llame a este método para recuperar los datos de varias cadenas para un nombre de valor especificado.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Llame a este método para recuperar los datos QWORD para un nombre de valor especificado.|
|[CRegKey::QueryStringValue](#querystringvalue)|Llame a este método para recuperar los datos de cadena para un nombre de valor especificado.|
|[CRegKey::QueryValue](#queryvalue)|Llame a este método para recuperar los datos del campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Llame a este método para quitar la clave especificada del registro y quitar explícitamente las subclaves.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Llame a este método para establecer el valor binario de la clave del Registro.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Llame a este método para establecer el valor DWORD de la clave del Registro.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Llame a este método para establecer el valor GUID de la clave del Registro.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Llame a este método para establecer la seguridad de la clave del Registro.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Llame a este método para almacenar datos en un campo de valor especificado de una clave especificada.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Llame a este método para establecer el valor de varias cadenas de la clave del Registro.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Llame a este método para establecer el valor QWORD de la clave del Registro.|
|[CRegKey::SetStringValue](#setstringvalue)|Llame a este método para establecer el valor de cadena de la clave del Registro.|
|[CRegKey::SetValue](#setvalue)|Llame a este método para almacenar datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRegKey::operador HKEY](#operator_hkey)|Convierte un `CRegKey` objeto en un HKEY.|
|[CRegKey::operador ?](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Contiene un identificador de la `CRegKey` clave del Registro asociada al objeto.|
|[CRegKey::m_pTM](#m_ptm)|Puntero `CAtlTransactionManager` al objeto|

## <a name="remarks"></a>Observaciones

`CRegKey`proporciona métodos para crear y eliminar claves y valores en el registro del sistema. El registro contiene un conjunto específico de definiciones de instalación para los componentes del sistema, como números de versión de software, asignaciones lógicos a físicas de hardware instalado y objetos COM.

`CRegKey`proporciona una interfaz de programación al registro del sistema para una máquina determinada. Por ejemplo, para abrir una `CRegKey::Open`clave de registro determinada, llame a . Para recuperar o modificar un `CRegKey::QueryValue` `CRegKey::SetValue`valor de datos, llame o , respectivamente. Para cerrar una `CRegKey::Close`clave, llame a .

Al cerrar una clave, sus datos del registro se escriben (se vacían) en el disco duro. Este proceso puede tardar varios segundos. Si la aplicación debe escribir explícitamente los datos del Registro en el disco duro, puede llamar a la función [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32. Sin `RegFlushKey` embargo, utiliza muchos recursos del sistema y debe llamarse sólo cuando sea absolutamente necesario.

> [!IMPORTANT]
> Los métodos que permiten al autor de la llamada especificar una ubicación del Registro tienen el potencial de leer datos que no se pueden confiar. Los métodos que hacen uso de [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) deben tener en cuenta que esta función no controla explícitamente las cadenas que son NULL terminado. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey::Attach

Llame a este método para `CRegKey` asociar un HKEY al objeto estableciendo el identificador de miembro [m_hKey](#m_hkey) en *hKey*.

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
El identificador de una clave del Registro.

### <a name="remarks"></a>Observaciones

`Attach`afirmará `m_hKey` si no es NULL.

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey::Cerrar

Llame a este método para liberar el identificador de miembro [m_hKey](#m_hkey) y establecerlo en NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario devuelve un valor de error.

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey::Create

Llame a este método para crear la clave especificada, si no existe como una subclave de *hKeyParent*.

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*hKeyParent*<br/>
El identificador de una llave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*lpszClass*<br/>
Especifica la clase de la clave que se va a crear o abrir. El valor predeterminado es REG_NONE.

*dwOptions*<br/>
Opciones para la clave. El valor predeterminado es REG_OPTION_NON_VOLATILE. Para obtener una lista de posibles valores y descripciones, vea [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) en el Windows SDK.

*samDesired*<br/>
El acceso de seguridad de la clave. El valor predeterminado es KEY_READ KEY_WRITE &#124;. Para obtener una lista de los `RegCreateKeyEx`valores y descripciones posibles, consulte .

*lpSecAttr*<br/>
Puntero a una estructura [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que indica si un proceso secundario puede heredar el identificador de la clave. De forma predeterminada, este parámetro es NULL (lo que significa que el identificador no se puede heredar).

*lpdwDisposition*<br/>
[fuera] Si no es NULL, recupera REG_CREATED_NEW_KEY (si la clave no existía y se creó) o REG_OPENED_EXISTING_KEY (si la clave existía y se abrió).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS y abre la clave. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

`Create`establece el miembro [m_hKey](#m_hkey) en el identificador de esta clave.

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey::CRegKey

El constructor.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Referencia a un objeto `CRegKey`.

*hKey*<br/>
Identificador de una clave del Registro.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

Crea un nuevo objeto `CRegKey`. El objeto se puede `CRegKey` crear desde un objeto existente o desde un identificador a una clave del Registro.

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey::-CRegKey

Destructor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Observaciones

El destructor `m_hKey`libera .

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

Llame a este método para quitar la clave especificada del registro.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parámetros

*lpszSubKey*<br/>
Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

`DeleteSubKey`solo puede eliminar una clave que no tiene subclaves. Si la clave tiene subclaves, llame a [RecurseDeleteKey](#recursedeletekey) en su lugar.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::DeleteValue

Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parámetros

*lpszValue*<br/>
Especifica el campo de valor que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::Detach

Llame a este método para separar `CRegKey` el identificador `m_hKey` de miembro [m_hKey](#m_hkey) del objeto y establecerlo en NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

La clave HKEY `CRegKey` asociada al objeto.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CRegKey::EnumKey

Llame a este método para enumerar las subclaves de la clave de registro abierta.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
El índice de subclaves. Este parámetro debe ser cero para la primera llamada y luego incrementado para las llamadas subsiguientes

*pszName*<br/>
Puntero a un búfer que recibe el nombre de la subclave, incluido el carácter nulo de terminación. Solo el nombre de la subclave se copia en el búfer, no en la jerarquía de claves completa.

*pnNameLength*<br/>
Puntero a una variable que especifica el tamaño, en TCHARs, del búfer especificado por el *pszName* parámetro. Este tamaño debe incluir el carácter nulo de terminación. Cuando el método devuelve, la variable señalada por *pnNameLength* contiene el número de caracteres almacenados en el búfer. El recuento devuelto no incluye el carácter nulo de terminación.

*pftLastWriteTime*<br/>
Puntero a una variable que recibe la última vez que se escribió la subclave enumerada.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Para enumerar las subclaves, llame `CRegKey::EnumKey` con un índice de cero. Incremente el valor del índice y repita hasta que el método devuelva ERROR_NO_MORE_ITEMS. Para obtener más información, consulte [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) en el Windows SDK.

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::Flush

Llame a este método para escribir todos los atributos de la clave de registro abierta en el registro.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) en el Windows SDK.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey::GetKeySecurity

Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave de registro abierta.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
El [valor SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) que indica la información de seguridad solicitada.

*Psd*<br/>
Puntero a un búfer que recibe una copia del descriptor de seguridad solicitado.

*pnBytes*<br/>
El tamaño, en bytes, del búfer al que apunta *psd*.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero se define en WINERROR. H.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey::m_hKey

Contiene un identificador de la `CRegKey` clave del Registro asociada al objeto.

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey::m_pTM

Puntero a `CAtlTransactionManager` un objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Observaciones

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

Este método notifica al autor de la llamada acerca de los cambios en los atributos o el contenido de la clave de registro abierta.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parámetros

*bWatchSubtree*<br/>
Especifica una marca que indica si se deben notificar los cambios en la clave especificada y todas sus subclaves o solo en la clave especificada. Si este parámetro es TRUE, el método notifica los cambios en la clave y sus subclaves. Si el parámetro es FALSE, el método notifica los cambios solo en la clave.

*dwNotifyFilter*<br/>
Especifica un conjunto de indicadores que controlan qué cambios se deben notificar. Este parámetro puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Notifique al autor de la llamada si se agrega o elimina una subclave.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Notifique al autor de la llamada los cambios en los atributos de la clave, como la información del descriptor de seguridad.|
|REG_NOTIFY_CHANGE_LAST_SET|Notifique al autor de la llamada los cambios en un valor de la clave. Esto puede incluir agregar o eliminar un valor o cambiar un valor existente.|
|REG_NOTIFY_CHANGE_SECURITY|Notifique al autor de la llamada los cambios en el descriptor de seguridad de la clave.|

*hEvent*<br/>
Identificador para un evento. Si el *bAsync* parámetro es TRUE, el método devuelve inmediatamente y los cambios se notifican mediante la señalización de este evento. Si *bAsync* es FALSE, se omite *hEvent.*

*bAsync*<br/>
Especifica una marca que indica cómo cambia el método. Si este parámetro es TRUE, el método devuelve inmediatamente y notifica los cambios señalando el evento especificado. Cuando este parámetro es FALSE, el método no devuelve hasta que se ha producido un cambio. Si *hEvent* no especifica un evento válido, el parámetro *bAsync* no puede ser TRUE.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Este método no notifica al autor de la llamada si se elimina la clave especificada.

Para obtener más información y un programa de ejemplo, vea [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::Open

Llame a este método para abrir la clave especificada y establecer [m_hKey](#m_hkey) en el identificador de esta clave.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parámetros

*hKeyParent*<br/>
El identificador de una llave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*samDesired*<br/>
El acceso de seguridad de la clave. El valor predeterminado es KEY_ALL_ACCESS. Para obtener una lista de posibles valores y descripciones, vea [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un valor de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Si el parámetro *lpszKeyName* es NULL o `Open` apunta a una cadena vacía, abre un nuevo identificador de la clave identificada por *hKeyParent*, pero no cierra ningún identificador abierto anteriormente.

A diferencia de [CRegKey::Create](#create), `Open` no creará la clave especificada si no existe.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::operador HKEY

Convierte un `CRegKey` objeto en un HKEY.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::operador ?

Operador de asignación.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave que se debe copiar.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la nueva clave.

### <a name="remarks"></a>Observaciones

Este operador separa la *clave* de su objeto `CRegKey` actual y la asigna al objeto en su lugar.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

Llame a este método para recuperar los datos binarios para un nombre de valor especificado.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*pValue*<br/>
Puntero a un búfer que recibe los datos del valor.

*pnBytes*<br/>
Puntero a una variable que especifica el tamaño, en bytes, del búfer al que apunta el parámetro *pValue.* Cuando se devuelve el método, esta variable contiene el tamaño de los datos copiados en el búfer.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son de tipo REG_BINARY, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Observaciones

Este método hace `RegQueryValueEx` uso de y confirma que se devuelve el tipo correcto de datos. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

Llame a este método para recuperar los datos DWORD para un nombre de valor especificado.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*dwValue*<br/>
Puntero a un búfer que recibe el DWORD.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son de tipo REG_DWORD, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Observaciones

Este método hace `RegQueryValueEx` uso de y confirma que se devuelve el tipo correcto de datos. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

Llame a este método para recuperar los datos GUID para un nombre de valor especificado.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*guidValue*<br/>
Puntero a una variable que recibe el GUID.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son un GUID válido, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Observaciones

Este método hace `CRegKey::QueryStringValue` uso de y convierte la cadena en un GUID mediante [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

Llame a este método para recuperar los datos de varias cadenas para un nombre de valor especificado.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*pszValue*<br/>
Puntero a un búfer que recibe los datos de varias cadenas. Una cadena múltiple es una matriz de cadenas terminadas en null, terminadas por dos caracteres nulos.

*pnChars*<br/>
El tamaño, en TCANRs, del búfer al que apunta *pszValue*. Cuando se devuelve el método, *pnChars* contiene el tamaño, en TCAN, de la cadena múltiple recuperada, incluido un carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son de tipo REG_MULTI_SZ, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Observaciones

Este método hace `RegQueryValueEx` uso de y confirma que se devuelve el tipo correcto de datos. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

Llame a este método para recuperar los datos QWORD para un nombre de valor especificado.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*qwValue*<br/>
Puntero a un búfer que recibe el QWORD.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son de tipo REG_QWORD, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Observaciones

Este método hace `RegQueryValueEx` uso de y confirma que se devuelve el tipo correcto de datos. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey::QueryStringValue

Llame a este método para recuperar los datos de cadena para un nombre de valor especificado.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*pszValue*<br/>
Puntero a un búfer que recibe los datos de cadena.

*pnChars*<br/>
El tamaño, en TCANRs, del búfer al que apunta *pszValue*. Cuando se devuelve el método, *pnChars* contiene el tamaño, en TCAN, de la cadena recuperada, incluido un carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. H. Si los datos a los que se hace referencia no son de tipo REG_SZ, se devuelve ERROR_INVALID_DATA. Si el método devuelve ERROR_MORE_DATA, *pnChars* es igual a cero, no el tamaño de búfer necesario en bytes.

### <a name="remarks"></a>Observaciones

Este método hace `RegQueryValueEx` uso de y confirma que se devuelve el tipo correcto de datos. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::QueryValue

Llame a este método para recuperar los datos del campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar. Si *pszValueName* es NULL o una cadena vacía, "", el método recupera el tipo y los datos para el valor predeterminado o sin nombre de la clave, si existe.

*pdwType*<br/>
Puntero a una variable que recibe un código que indica el tipo de datos almacenados en el valor especificado. El *pdwType* parámetro puede ser NULL si el código de tipo no es necesario.

*pData*<br/>
Puntero a un búfer que recibe los datos del valor. Este parámetro puede ser NULL si los datos no son necesarios.

*pnBytes*<br/>
Puntero a una variable que especifica el tamaño, en bytes, del búfer al que apunta el *pData* parámetro. Cuando se devuelve el método, esta variable contiene el tamaño de los datos copiados en *pData.*

*dwValue*<br/>
Datos numéricos del campo de valor.

*lpszValueName*<br/>
Especifica el campo de valor que se va a consultar.

*szValue*<br/>
Datos de cadena del campo de valor.

*pdwCount*<br/>
El tamaño de los datos de cadena. Su valor se establece inicialmente en el tamaño del búfer *szValue.*

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Las dos versiones originales de `QueryValue` ya no son compatibles y se marcan como ATL_DEPRECATED. El compilador emitirá una advertencia si se usan estos formularios.

El método restante llama a RegQueryValueEx.

> [!IMPORTANT]
> Este método permite al autor de la llamada especificar cualquier ubicación del registro, lo que puede leer datos que no se pueden confiar. Además, la función RegQueryValueEx utilizada por este método no controla explícitamente las cadenas que terminan NULL. Ambas condiciones deben comprobarse mediante el código de llamada.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

Llame a este método para quitar la clave especificada del registro y quitar explícitamente las subclaves.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parámetros

*lpszKey*<br/>
Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un valor de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Si la clave tiene subclaves, debe llamar a este método para eliminar la clave.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

Llame a este método para establecer el valor binario de la clave del Registro.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*pValue*<br/>
Puntero a un búfer que contiene los datos que se van a almacenar con el nombre de valor especificado.

*nBytes*<br/>
Especifica el tamaño, en bytes, de la información señalada por el *pValue* parámetro.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método utiliza [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CRegKey::SetDWORDValue

Llame a este método para establecer el valor DWORD de la clave del Registro.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*dwValue*<br/>
Los datos DWORD que se almacenarán con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método utiliza [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey::SetGUIDValue

Llame a este método para establecer el valor GUID de la clave del Registro.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*guidValue*<br/>
Referencia al GUID que se va a almacenar con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método hace `CRegKey::SetStringValue` uso y convierte el GUID en una cadena mediante [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey::SetKeyValue

Llame a este método para almacenar datos en un campo de valor especificado de una clave especificada.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*lpszKeyName*<br/>
Especifica el nombre de la clave que se va a crear o abrir. Este nombre debe ser una subclave de [m_hKey](#m_hkey).

*lpszValue*<br/>
Especifica los datos que se van a almacenar. Este parámetro debe ser no NULL.

*lpszValueName*<br/>
Especifica el campo de valor que se va a establecer. Si aún no existe un campo de valor con este nombre en la clave, se agrega.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Llame a este método para crear o abrir la clave *lpszKeyName* y almacenar los datos *lpszValue* en el campo de valor *lpszValueName.*

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::SetKeySecurity

Llame a este método para establecer la seguridad de la clave del Registro.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Especifica los componentes del descriptor de seguridad que se va a establecer. El valor puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Establece la lista de control de acceso discrecional (DACL) de la clave. La clave debe tener acceso WRITE_DAC o el proceso de llamada debe ser el propietario del objeto.|
|GROUP_SECURITY_INFORMATION|Establece el identificador de seguridad de grupo principal (SID) de la clave. La clave debe tener acceso WRITE_OWNER o el proceso de llamada debe ser el propietario del objeto.|
|OWNER_SECURITY_INFORMATION|Establece el SID propietario de la clave. La clave debe tener acceso WRITE_OWNER, o el proceso de llamada debe ser el propietario del objeto o tener el privilegio SE_TAKE_OWNERSHIP_NAME habilitado.|
|SACL_SECURITY_INFORMATION|Establece la lista de control de acceso del sistema (SACL) de la clave. La clave debe tener acceso ACCESS_SYSTEM_SECURITY. La forma correcta de obtener este acceso es habilitar el [privilegio](/windows/win32/secauthz/privileges) SE_SECURITY_NAME en el token de acceso actual del autor de la llamada, abrir el identificador para el acceso ACCESS_SYSTEM_SECURITY y, a continuación, deshabilitar el privilegio.|

*Psd*<br/>
Puntero a una estructura [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) que especifica los atributos de seguridad que se establecerán para la clave especificada.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Establece los atributos de seguridad de la clave. Consulte [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) para obtener más detalles.

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

Llame a este método para establecer el valor de varias cadenas de la clave del Registro.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*pszValue*<br/>
Puntero a los datos de varias cadenas que se almacenarán con el nombre de valor especificado. Una cadena múltiple es una matriz de cadenas terminadas en null, terminadas por dos caracteres nulos.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método utiliza [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::SetQWORDValue

Llame a este método para establecer el valor QWORD de la clave del Registro.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*qwValue*<br/>
Los datos QWORD que se almacenarán con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método utiliza [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::SetStringValue

Llame a este método para establecer el valor de cadena de la clave del Registro.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente, el método lo agrega a la clave.

*pszValue*<br/>
Puntero a los datos de cadena que se van a almacenar con el nombre de valor especificado.

*dwType*<br/>
El tipo de la cadena que se va a escribir en el registro: REG_SZ (valor predeterminado) o REG_EXPAND_SZ (para cadenas múltiples).

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Este método utiliza [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::SetValue

Llame a este método para almacenar datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre aún no está presente en la clave, el método lo agrega a la clave. Si *pszValueName* es NULL o una cadena vacía, "", el método establece el tipo y los datos para el valor predeterminado o sin nombre de la clave.

*dwType*<br/>
Especifica un código que indica el tipo de datos al que apunta el *pValue* parámetro.

*pValue*<br/>
Puntero a un búfer que contiene los datos que se van a almacenar con el nombre de valor especificado.

*nBytes*<br/>
Especifica el tamaño, en bytes, de la información señalada por el *pValue* parámetro. Si los datos son de tipo REG_SZ, REG_EXPAND_SZ o REG_MULTI_SZ, *nBytes* debe incluir el tamaño del carácter nulo de terminación.

*hKeyParent*<br/>
El identificador de una llave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*lpszValue*<br/>
Especifica los datos que se van a almacenar. Este parámetro debe ser no NULL.

*lpszValueName*<br/>
Especifica el campo de valor que se va a establecer. Si aún no existe un campo de valor con este nombre en la clave, se agrega.

*dwValue*<br/>
Especifica los datos que se van a almacenar.

*bMulti*<br/>
Si es false, indica que la cadena es de tipo REG_SZ. Si es true, indica que la cadena es una cadena múltiple de tipo REG_MULTI_SZ.

*nValueLen*<br/>
Si *bMulti* es true, *nValueLen* es la longitud de la cadena *lpszValue* en caracteres. Si *bMulti* es false, un valor de -1 indica que el método calculará la longitud automáticamente.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un código de error distinto de cero definido en WINERROR. H.

### <a name="remarks"></a>Observaciones

Las dos versiones originales de `SetValue` están marcadas como ATL_DEPRECATED y ya no deben utilizarse. El compilador emitirá una advertencia si se usan estos formularios.

El tercer método llama a [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Vea también

[Muestra DCOM](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
