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
ms.openlocfilehash: 3faf446f74577034a3d0676b90ebe7027ef6da06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496538"
---
# <a name="cregkey-class"></a>Clase CRegKey

Esta clase proporciona métodos para manipular entradas en el registro del sistema.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CRegKey
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|El constructor.|
|[CRegKey::~CRegKey](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRegKey::Attach](#attach)|Llame a este método para adjuntar un `CRegKey` HKEY al objeto estableciendo el identificador de miembro `hKey`de [m_hKey](#m_hkey) en.|
|[CRegKey::Close](#close)|Llame a este método para liberar el identificador del miembro [m_hKey](#m_hkey) y ESTABLÉZCALO en NULL.|
|[CRegKey::Create](#create)|Llame a este método para crear la clave especificada, si no existe como subclave de `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Llame a este método para quitar la clave especificada del registro.|
|[CRegKey::DeleteValue](#deletevalue)|Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Llame a este método para desasociar el identificador de `CRegKey` miembro [m_hKey](#m_hkey) del `m_hKey` objeto y establecer en NULL.|
|[CRegKey::EnumKey](#enumkey)|Llame a este método para enumerar las subclaves de la clave del registro abierta.|
|[CRegKey::Flush](#flush)|Llame a este método para escribir todos los atributos de la clave del registro Open en el registro.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Este método notifica al llamador los cambios realizados en los atributos o en el contenido de la clave del registro abierta.|
|[CRegKey::Open](#open)|Llame a este método para abrir la clave especificada y establezca [m_hKey](#m_hkey) en el identificador de esta clave.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Llame a este método para recuperar los datos binarios de un nombre de valor especificado.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Llame a este método para recuperar los datos DWORD para un nombre de valor especificado.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Llame a este método para recuperar los datos de GUID para un nombre de valor especificado.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Llame a este método para recuperar los datos de multicadena para un nombre de valor especificado.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Llame a este método para recuperar los datos de QWORD para un nombre de valor especificado.|
|[CRegKey::QueryStringValue](#querystringvalue)|Llame a este método para recuperar los datos de cadena para un nombre de valor especificado.|
|[CRegKey::QueryValue](#queryvalue)|Llame a este método para recuperar los datos para el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Llame a este método para quitar la clave especificada del registro y quitar explícitamente las subclaves.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Llame a este método para establecer el valor binario de la clave del registro.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Llame a este método para establecer el valor DWORD de la clave del registro.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Llame a este método para establecer el valor GUID de la clave del registro.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Llame a este método para establecer la seguridad de la clave del registro.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Llame a este método para almacenar los datos en un campo de valor especificado de una clave especificada.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Llame a este método para establecer el valor de cadena de la clave del registro.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Llame a este método para establecer el valor QWORD de la clave del registro.|
|[CRegKey::SetStringValue](#setstringvalue)|Llame a este método para establecer el valor de cadena de la clave del registro.|
|[CRegKey::SetValue](#setvalue)|Llame a este método para almacenar los datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRegKey:: Operator HKEY](#operator_hkey)|Convierte un `CRegKey` objeto en HKEY.|
|[CRegKey::operator =](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Contiene un identificador de la clave del registro asociada al `CRegKey` objeto.|
|[CRegKey::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto|

## <a name="remarks"></a>Comentarios

`CRegKey`proporciona métodos para crear y eliminar claves y valores en el registro del sistema. El registro contiene un conjunto específico de instalación de definiciones para los componentes del sistema, como los números de versión de software, las asignaciones lógicas a físico del hardware instalado y los objetos COM.

`CRegKey`proporciona una interfaz de programación al registro del sistema para un equipo determinado. Por ejemplo, para abrir una clave del registro determinada, `CRegKey::Open`llame a. Para recuperar o modificar un valor de datos, `CRegKey::QueryValue` llame `CRegKey::SetValue`a o, respectivamente. Para cerrar una clave, llame `CRegKey::Close`a.

Al cerrar una clave, los datos del registro se escriben (se vacían) en el disco duro. Este proceso puede tardar varios segundos. Si la aplicación debe escribir explícitamente los datos del registro en el disco duro, puede llamar a la función [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) de Win32. Sin embargo `RegFlushKey` , utiliza muchos recursos del sistema y solo se debe llamar cuando sea absolutamente necesario.

> [!IMPORTANT]
>  Cualquier método que permita al llamador especificar una ubicación del registro tiene la posibilidad de leer los datos que no son de confianza. Los métodos que usan [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) deben tener en cuenta que esta función no controla explícitamente las cadenas que están terminadas en NULL. El código de llamada debe comprobar ambas condiciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="attach"></a>  CRegKey::Attach

Llame a este método para adjuntar un `CRegKey` HKEY al objeto estableciendo el identificador del miembro [m_hKey](#m_hkey) en *HKEY*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro.

### <a name="remarks"></a>Comentarios

`Attach`validará si `m_hKey` no es NULL.

##  <a name="close"></a>CRegKey:: Close

Llame a este método para liberar el identificador del miembro [m_hKey](#m_hkey) y ESTABLÉZCALO en NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, devuelve un valor de error.

##  <a name="create"></a>  CRegKey::Create

Llame a este método para crear la clave especificada, si no existe como subclave de *hKeyParent*.

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
Identificador de una clave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*lpszClass*<br/>
Especifica la clase de la clave que se va a crear o abrir. El valor predeterminado es REG_NONE.

*dwOptions*<br/>
Opciones de la clave. El valor predeterminado es REG_OPTION_NON_VOLATILE. Para obtener una lista de valores y descripciones posibles, vea [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) en el Windows SDK.

*samDesired*<br/>
Acceso de seguridad para la clave. El valor predeterminado es KEY_READ &#124; KEY_WRITE. Para obtener una lista de valores y descripciones `RegCreateKeyEx`posibles, vea.

*lpSecAttr*<br/>
Puntero a una estructura [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que indica si un proceso secundario puede heredar el identificador de la clave. De forma predeterminada, este parámetro es NULL (lo que significa que el identificador no se puede heredar).

*lpdwDisposition*<br/>
enuncia Si no es NULL, recupera REG_CREATED_NEW_KEY (si la clave no existía y se creó) o REG_OPENED_EXISTING_KEY (si la clave existía y se abrió).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS y abre la clave. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

`Create`establece el miembro [m_hKey](#m_hkey) en el identificador de esta clave.

##  <a name="cregkey"></a>  CRegKey::CRegKey

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
Identificador de una clave del registro.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

Crea un nuevo objeto `CRegKey`. El objeto se puede crear a partir de `CRegKey` un objeto existente o de un identificador a una clave del registro.

##  <a name="dtor"></a>  CRegKey::~CRegKey

Destructor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Comentarios

El destructor libera `m_hKey`.

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

Llame a este método para quitar la clave especificada del registro.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parámetros

*lpszSubKey*<br/>
Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

`DeleteSubKey`solo se puede eliminar una clave que no tenga subclaves. Si la clave tiene subclaves, llame a [RecurseDeleteKey](#recursedeletekey) en su lugar.

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parámetros

*lpszValue*<br/>
Especifica el campo de valor que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

##  <a name="detach"></a>  CRegKey::Detach

Llame a este método para desasociar el identificador de `CRegKey` miembro [m_hKey](#m_hkey) del `m_hKey` objeto y establecer en NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

HKEY asociado al `CRegKey` objeto.

##  <a name="enumkey"></a>  CRegKey::EnumKey

Llame a este método para enumerar las subclaves de la clave del registro abierta.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
Índice de la subclave. Este parámetro debe ser cero para la primera llamada y, a continuación, incrementarse en las llamadas posteriores

*pszName*<br/>
Puntero a un búfer que recibe el nombre de la subclave, incluido el carácter nulo de terminación. Solo el nombre de la subclave se copia en el búfer, no en la jerarquía de claves completa.

*pnNameLength*<br/>
Puntero a una variable que especifica el tamaño, en TCHARs, del búfer especificado por el parámetro *pszName empiezan* . Este tamaño debe incluir el carácter nulo de terminación. Cuando el método devuelve, la variable a la que apunta *pnNameLength* contiene el número de caracteres almacenados en el búfer. El recuento devuelto no incluye el carácter nulo de terminación.

*pftLastWriteTime*<br/>
Puntero a una variable que recibe la hora en que se escribió por última vez en la subclave enumerada.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Para enumerar las subclaves, `CRegKey::EnumKey` llame a con un índice de cero. Incremente el valor de índice y repita hasta que el método devuelva ERROR_NO_MORE_ITEMS. Para obtener más información, vea [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) en el Windows SDK.

##  <a name="flush"></a>  CRegKey::Flush

Llame a este método para escribir todos los atributos de la clave del registro Open en el registro.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) en el Windows SDK.

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Valor de [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) que indica la información de seguridad solicitada.

*psd*<br/>
Un puntero a un búfer que recibe una copia del descriptor de seguridad solicitado.

*pnBytes*<br/>
Tamaño, en bytes, del búfer al que apunta *PSD*.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero, que se define en WINERROR. C.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Contiene un identificador de la clave del registro asociada al `CRegKey` objeto.

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Comentarios

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

Este método notifica al llamador los cambios realizados en los atributos o en el contenido de la clave del registro abierta.

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
Especifica un conjunto de marcas que controlan los cambios que se deben informar. Este parámetro puede ser una combinación de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Notificar al autor de la llamada si se agrega o elimina una subclave.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Notifique al llamador los cambios realizados en los atributos de la clave, como la información del descriptor de seguridad.|
|REG_NOTIFY_CHANGE_LAST_SET|Notifique al llamador los cambios realizados en un valor de la clave. Esto puede incluir agregar o eliminar un valor o cambiar un valor existente.|
|REG_NOTIFY_CHANGE_SECURITY|Notifique al llamador los cambios realizados en el descriptor de seguridad de la clave.|

*hEvent*<br/>
Identificador para un evento. Si el parámetro *bAsync* es true, el método vuelve inmediatamente y se indica que los cambios señalan este evento. Si *bAsync* es false, *hEvent* se omite.

*bAsync*<br/>
Especifica una marca que indica el modo en que el método notifica los cambios. Si este parámetro es TRUE, el método devuelve inmediatamente y notifica los cambios señalando el evento especificado. Cuando este parámetro es FALSE, el método no devuelve ningún resultado hasta que se ha producido un cambio. Si *hEvent* no especifica un evento válido, el parámetro *bAsync* no puede ser true.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Este método no notifica al llamador si se elimina la clave especificada.

Para obtener más información y un programa de ejemplo, vea [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>  CRegKey::Open

Llame a este método para abrir la clave especificada y establezca [m_hKey](#m_hkey) en el identificador de esta clave.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parámetros

*hKeyParent*<br/>
Identificador de una clave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*samDesired*<br/>
Acceso de seguridad para la clave. El valor predeterminado es KEY_ALL_ACCESS. Para obtener una lista de valores y descripciones posibles, vea [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un valor de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Si el parámetro *lpszKeyName* es null o apunta a una cadena vacía, `Open` abre un nuevo identificador de la clave identificado por *hKeyParent*, pero no cierra ningún controlador abierto previamente.

A diferencia de [CRegKey:: Create](#create), `Open` no creará la clave especificada si no existe.

##  <a name="operator_hkey"></a>CRegKey:: Operator HKEY

Convierte un `CRegKey` objeto en HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: Operator =

Operador de asignación.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a la nueva clave.

### <a name="remarks"></a>Comentarios

Este operador desasocia la *clave* de su objeto actual y la `CRegKey` asigna al objeto en su lugar.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Llame a este método para recuperar los datos binarios de un nombre de valor especificado.

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
Puntero a una variable que especifica el tamaño, en bytes, del búfer al que apunta el parámetro *pValue* . Cuando el método devuelve, esta variable contiene el tamaño de los datos copiados en el búfer.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son del tipo REG_BINARY, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Comentarios

Este método usa `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

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

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son del tipo REG_DWORD, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Comentarios

Este método usa `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Llame a este método para recuperar los datos de GUID para un nombre de valor especificado.

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

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son un GUID válido, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Comentarios

Este método usa `CRegKey::QueryStringValue` y convierte la cadena en un GUID mediante [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Llame a este método para recuperar los datos de multicadena para un nombre de valor especificado.

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
Puntero a un búfer que recibe los datos de multicadena. Una multicadena es una matriz de cadenas terminadas en null, terminada con dos caracteres null.

*pnChars*<br/>
Tamaño, en TCHARs, del búfer al que apunta *pszValue*. Cuando el método devuelve, *pnChars* contiene el tamaño, en TCHARs, de la multistring recuperada, incluido un carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son del tipo REG_MULTI_SZ, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Comentarios

Este método usa `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Llame a este método para recuperar los datos de QWORD para un nombre de valor especificado.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar.

*qwValue*<br/>
Puntero a un búfer que recibe QWORD.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son del tipo REG_QWORD, se devuelve ERROR_INVALID_DATA.

### <a name="remarks"></a>Comentarios

Este método usa `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

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
Puntero a un búfer que recibe los datos de la cadena.

*pnChars*<br/>
Tamaño, en TCHARs, del búfer al que apunta *pszValue*. Cuando el método devuelve, *pnChars* contiene el tamaño, en TCHARs, de la cadena recuperada, incluido un carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en WINERROR. C. Si los datos a los que se hace referencia no son del tipo REG_SZ, se devuelve ERROR_INVALID_DATA. Si el método devuelve ERROR_MORE_DATA, *pnChars* es igual a cero, no al tamaño de búfer necesario en bytes.

### <a name="remarks"></a>Comentarios

Este método usa `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) para obtener más detalles.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Llame a este método para recuperar los datos para el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.

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
Puntero a una cadena terminada en null que contiene el nombre del valor que se va a consultar. Si *pszValueName* es null o una cadena vacía, "", el método recupera el tipo y los datos para el valor sin nombre o predeterminado de la clave, si existe.

*pdwType*<br/>
Puntero a una variable que recibe un código que indica el tipo de datos almacenados en el valor especificado. El parámetro *pdwType* puede ser null si no se requiere el código de tipo.

*pData*<br/>
Puntero a un búfer que recibe los datos del valor. Este parámetro puede ser NULL si los datos no son necesarios.

*pnBytes*<br/>
Puntero a una variable que especifica el tamaño, en bytes, del búfer al que apunta el parámetro *pdata* . Cuando el método devuelve, esta variable contiene el tamaño de los datos copiados en *pdata.*

*dwValue*<br/>
Datos numéricos del campo de valor.

*lpszValueName*<br/>
Especifica el campo de valor que se va a consultar.

*szValue*<br/>
Los datos de la cadena del campo de valor.

*pdwCount*<br/>
Tamaño de los datos de cadena. Su valor se establece inicialmente en el tamaño del búfer de *szValue* .

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, se definirá un código de error distinto de cero en WINERROR. C.

### <a name="remarks"></a>Comentarios

Las dos versiones originales de `QueryValue` ya no se admiten y se marcan como ATL_DEPRECATED. El compilador emitirá una advertencia si se usan estos formularios.

El método restante llama a RegQueryValueEx.

> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, con lo que se pueden leer datos que no son de confianza. Además, la función RegQueryValueEx usada por este método no controla explícitamente las cadenas que se terminan en NULL. El código de llamada debe comprobar ambas condiciones.

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

Llame a este método para quitar la clave especificada del registro y quitar explícitamente las subclaves.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parámetros

*lpszKey*<br/>
Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, un valor de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Si la clave tiene subclaves, debe llamar a este método para eliminar la clave.

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

Llame a este método para establecer el valor binario de la clave del registro.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*pValue*<br/>
Puntero a un búfer que contiene los datos que se van a almacenar con el nombre de valor especificado.

*nBytes*<br/>
Especifica el tamaño, en bytes, de la información a la que apunta el parámetro *pValue* .

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

Llame a este método para establecer el valor DWORD de la clave del registro.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*dwValue*<br/>
Datos DWORD que se van a almacenar con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

Llame a este método para establecer el valor GUID de la clave del registro.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*guidValue*<br/>
Referencia al GUID que se va a almacenar con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa `CRegKey::SetStringValue` y convierte el GUID en una cadena mediante [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

Llame a este método para almacenar los datos en un campo de valor especificado de una clave especificada.

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
Especifica los datos que se van a almacenar. Este parámetro no debe ser NULL.

*lpszValueName*<br/>
Especifica el campo de valor que se va a establecer. Si un campo de valor con este nombre aún no existe en la clave, se agrega.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, se definirá un código de error distinto de cero en WINERROR. C.

### <a name="remarks"></a>Comentarios

Llame a este método para crear o abrir la clave *lpszKeyName* y almacenar los datos de *lpszValue* en el campo de valor *lpszValueName* .

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

Llame a este método para establecer la seguridad de la clave del registro.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parámetros

*si*<br/>
Especifica los componentes del descriptor de seguridad que se van a establecer. El valor puede ser una combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Establece la lista de control de acceso discrecional (DACL) de la clave. La clave debe tener acceso a WRITE_DAC o el proceso de llamada debe ser el propietario del objeto.|
|GROUP_SECURITY_INFORMATION|Establece el identificador de seguridad (SID) del grupo principal de la clave. La clave debe tener el acceso de WRITE_OWNER o el proceso de llamada debe ser el propietario del objeto.|
|OWNER_SECURITY_INFORMATION|Establece el SID del propietario de la clave. La clave debe tener acceso a WRITE_OWNER, o el proceso de llamada debe ser el propietario del objeto o tener el privilegio SE_TAKE_OWNERSHIP_NAME habilitado.|
|SACL_SECURITY_INFORMATION|Establece la lista de control de acceso del sistema (SACL) de la clave. La clave debe tener acceso de ACCESS_SYSTEM_SECURITY. La manera adecuada de obtener este acceso es habilitar el [privilegio](/windows/win32/secauthz/privileges) SE_SECURITY_NAME en el token de acceso actual del llamador, abrir el identificador de acceso a ACCESS_SYSTEM_SECURITY y, a continuación, deshabilitar el privilegio.|

*psd*<br/>
Puntero a una estructura [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) que especifica los atributos de seguridad que se van a establecer para la clave especificada.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Establece los atributos de seguridad de la clave. Consulte [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) para obtener más información.

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

Llame a este método para establecer el valor de cadena de la clave del registro.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*pszValue*<br/>
Puntero a los datos de multicadena que se van a almacenar con el nombre de valor especificado. Una multicadena es una matriz de cadenas terminadas en null, terminada con dos caracteres null.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

Llame a este método para establecer el valor QWORD de la clave del registro.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*qwValue*<br/>
Datos de QWORD que se van a almacenar con el nombre de valor especificado.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

Llame a este método para establecer el valor de cadena de la clave del registro.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parámetros

*pszValueName*<br/>
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si no existe un valor con este nombre, el método lo agrega a la clave.

*pszValue*<br/>
Puntero a los datos de cadena que se van a almacenar con el nombre de valor especificado.

*dwType*<br/>
Tipo de la cadena que se va a escribir en el registro: REG_SZ (el valor predeterminado) o REG_EXPAND_SZ (para las cadenas multistring).

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en WINERROR. C.

### <a name="remarks"></a>Comentarios

Este método usa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) para escribir el valor en el registro.

##  <a name="setvalue"></a>  CRegKey::SetValue

Llame a este método para almacenar los datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.

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
Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre todavía no está presente en la clave, el método lo agrega a la clave. Si *pszValueName* es null o una cadena vacía, "", el método establece el tipo y los datos para el valor sin nombre o predeterminado de la clave.

*dwType*<br/>
Especifica un código que indica el tipo de datos a los que apunta el parámetro *pValue* .

*pValue*<br/>
Puntero a un búfer que contiene los datos que se van a almacenar con el nombre de valor especificado.

*nBytes*<br/>
Especifica el tamaño, en bytes, de la información a la que apunta el parámetro *pValue* . Si los datos son de tipo REG_SZ, REG_EXPAND_SZ o REG_MULTI_SZ, *nBytes* debe incluir el tamaño del carácter nulo de terminación.

*hKeyParent*<br/>
Identificador de una clave abierta.

*lpszKeyName*<br/>
Especifica el nombre de una clave que se va a crear o abrir. Este nombre debe ser una subclave de *hKeyParent*.

*lpszValue*<br/>
Especifica los datos que se van a almacenar. Este parámetro no debe ser NULL.

*lpszValueName*<br/>
Especifica el campo de valor que se va a establecer. Si un campo de valor con este nombre aún no existe en la clave, se agrega.

*dwValue*<br/>
Especifica los datos que se van a almacenar.

*bMulti*<br/>
Si es false, indica que la cadena es de tipo REG_SZ. Si es true, indica que la cadena es de tipo REG_MULTI_SZ.

*nValueLen*<br/>
Si *bMulti* es true, *nValueLen* es la longitud de la cadena *lpszValue* en caracteres. Si *bMulti* es false, el valor-1 indica que el método calculará la longitud automáticamente.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, se definirá un código de error distinto de cero en WINERROR. C.

### <a name="remarks"></a>Comentarios

Las dos versiones originales de `SetValue` se marcan como ATL_DEPRECATED y ya no deben usarse. El compilador emitirá una advertencia si se usan estos formularios.

El tercer método llama a [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Vea también

[Ejemplo DCOM](../../overview/visual-cpp-samples.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
