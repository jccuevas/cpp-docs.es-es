---
title: CRegKey (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe661f48c583cfb82e52b6c125f6cf7fce2e714
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203563"
---
# <a name="cregkey-class"></a>CRegKey (clase)
Esta clase proporciona métodos para manipular las entradas del registro del sistema.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CRegKey
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::CRegKey](#cregkey)|El constructor.|  
|[CRegKey:: ~ CRegKey](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::Attach](#attach)|Llame a este método para adjuntar un HKEY a la `CRegKey` objeto estableciendo la [m_hKey](#m_hkey) identificador de miembro `hKey`.|  
|[CRegKey::Close](#close)|Llame a este método para liberar el [m_hKey](#m_hkey) miembro controlar y establézcalo en NULL.|  
|[CRegKey::Create](#create)|Llame a este método para crear la clave especificada, si no existe como una subclave de `hKeyParent`.|  
|[CRegKey::DeleteSubKey](#deletesubkey)|Llame a este método para quitar la clave especificada del registro.|  
|[CRegKey::DeleteValue](#deletevalue)|Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).|  
|[CRegKey::Detach](#detach)|Llame a este método para separar el [m_hKey](#m_hkey) identificador de miembro desde el `CRegKey` de objeto y establecer `m_hKey` en NULL.|  
|[CRegKey::EnumKey](#enumkey)|Llame a este método para enumerar las subclaves de la clave del registro abierta.|  
|[CRegKey::Flush](#flush)|Llame a este método para escribir todos los atributos de la clave del registro abierta en el registro.|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Este método notifica al llamador sobre los cambios en los atributos o contenido de la clave del registro abierta.|  
|[CRegKey::Open](#open)|Llame a este método para abrir la clave especificada y establece [m_hKey](#m_hkey) al identificador de esta clave.|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Llame a este método para recuperar los datos binarios de un nombre de valor especificado.|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Llame a este método para recuperar los datos DWORD para un nombre de valor especificado.|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Llame a este método para recuperar los datos GUID para un nombre de valor especificado.|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Llame a este método para recuperar los datos multistring para un nombre de valor especificado.|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Llame a este método para recuperar los datos de tipo QWORD para un nombre de valor especificado.|  
|[CRegKey::QueryStringValue](#querystringvalue)|Llame a este método para recuperar los datos de cadena de un nombre de valor especificado.|  
|[CRegKey::QueryValue](#queryvalue)|Llame a este método para recuperar los datos para el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Llame a este método para quitar la clave especificada del registro y quitar explícitamente todas las subclaves.|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Llame a este método para establecer el valor binario de la clave del registro.|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|Llame a este método para establecer el valor DWORD de la clave del registro.|  
|[CRegKey::SetGUIDValue](#setguidvalue)|Llame a este método para establecer el valor GUID de la clave del registro.|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|Llame a este método para establecer la seguridad de la clave del registro.|  
|[CRegKey::SetKeyValue](#setkeyvalue)|Llame a este método para almacenar datos en un campo de valor especificado de una clave especificada.|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Llame a este método para establecer el valor multistring de la clave del registro.|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|Llame a este método para establecer el valor QWORD de la clave del registro.|  
|[CRegKey::SetStringValue](#setstringvalue)|Llame a este método para establecer el valor de cadena de la clave del registro.|  
|[CRegKey::SetValue](#setvalue)|Llame a este método para almacenar datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como ATL_DEPRECATED.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|Convierte un `CRegKey` objeto a un HKEY.|  
|[CRegKey::operator =](#operator_eq)|Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|Contiene un identificador de la clave del registro asociada con el `CRegKey` objeto.|  
|[CRegKey::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto|  
  
## <a name="remarks"></a>Comentarios  
 `CRegKey` Proporciona métodos para crear y eliminar claves y valores del registro del sistema. El registro contiene un conjunto específico de la instalación de definiciones para los componentes del sistema, como números de versión de software, las asignaciones lógicas a físicas de hardware instalado y objetos COM.  
  
 `CRegKey` Proporciona una interfaz de programación para el registro del sistema para un equipo determinado. Por ejemplo, para abrir una clave del Registro determinada, llame a `CRegKey::Open`. Para recuperar o modificar un valor de datos, llame a `CRegKey::QueryValue` o `CRegKey::SetValue`, respectivamente. Para cerrar una clave, llame a `CRegKey::Close`.  
  
 Cuando se cierra una clave, sus datos de registro se escriben (vaciado) en el disco duro. Este proceso puede tardar varios segundos. Si la aplicación debe escribir explícitamente los datos del registro en el disco duro, puede llamar a la [RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) función de Win32. Sin embargo, `RegFlushKey` utiliza muchos recursos del sistema y se debe llamar cuando sea absolutamente necesario.  
  
> [!IMPORTANT]
>  Los métodos que permiten al llamador especificar una ubicación del registro tienen el potencial para leer datos que no son de confianza. Métodos que hacen usan de [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) debería tener en cuenta que esta función no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="attach"></a>  CRegKey::Attach  
 Llame a este método para adjuntar un HKEY a la `CRegKey` objeto estableciendo la [m_hKey](#m_hkey) identificador de miembro *hKey*.  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *hKey*  
 El identificador de una clave del registro.  
  
### <a name="remarks"></a>Comentarios  
 `Attach` se producirá una aserción si `m_hKey` es distinto de NULL.  
  
##  <a name="close"></a>  CRegKey::Close  
 Llame a este método para liberar el [m_hKey](#m_hkey) miembro controlar y establézcalo en NULL.  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, devuelve un valor de error.  
  
##  <a name="create"></a>  CRegKey::Create  
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
 *hKeyParent*  
 El identificador de una clave abierta.  
  
 *lpszKeyName*  
 Especifica el nombre de una clave que se creó o se abran. Este nombre debe ser una subclave de *hKeyParent*.  
  
 *lpszClass*  
 Especifica la clase de la clave que se crea o se abre. El valor predeterminado es REG_NONE.  
  
 *dwOptions*  
 Opciones de la clave. El valor predeterminado es REG_OPTION_NON_VOLATILE. Para obtener una lista de posibles valores y descripciones, consulte [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) en el SDK de Windows.  
  
 *samDesired*  
 El acceso de seguridad para la clave. El valor predeterminado es KEY_READ &#124; KEY_WRITE. Para obtener una lista de posibles valores y descripciones, consulte `RegCreateKeyEx`.  
  
 *lpSecAttr*  
 Un puntero a un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que indica si un proceso secundario puede heredar el identificador de la clave. De forma predeterminada, este parámetro es NULL (es decir, no se puede heredar el identificador).  
  
 *lpdwDisposition*  
 [out] Si no es NULL, recupera REG_CREATED_NEW_KEY (si la clave no existía y se ha creado) o REG_OPENED_EXISTING_KEY (si la clave existía y se ha abierto).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS y abre la clave. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 `Create` establece el [m_hKey](#m_hkey) miembro para el identificador de esta clave.  
  
##  <a name="cregkey"></a>  CRegKey::CRegKey  
 El constructor.  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *key*  
 Referencia a un objeto `CRegKey`.  
  
 *hKey*  
 Identificador de una clave del registro.  
  
 *pTM*  
 Puntero al objeto CAtlTransactionManager  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo objeto `CRegKey`. El objeto se puede crear a partir de una máquina `CRegKey` objeto, o desde un identificador de una clave del registro.  
  
##  <a name="dtor"></a>  CRegKey:: ~ CRegKey  
 Destructor.  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Las versiones de destructor `m_hKey`.  
  
##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey  
 Llame a este método para quitar la clave especificada del registro.  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSubKey*  
 Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 `DeleteSubKey` solo se puede eliminar una clave que tenga subclaves. Si la clave tiene subclaves, llame a [RecurseDeleteKey](#recursedeletekey) en su lugar.  
  
##  <a name="deletevalue"></a>  CRegKey::DeleteValue  
 Llame a este método para quitar un campo de valor de [m_hKey](#m_hkey).  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszValue*  
 Especifica el campo de valor para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
##  <a name="detach"></a>  CRegKey::Detach  
 Llame a este método para separar el [m_hKey](#m_hkey) identificador de miembro desde el `CRegKey` de objeto y establecer `m_hKey` en NULL.  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 HKEY que se va asociado con el `CRegKey` objeto.  
  
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
 *iÍndice*  
 El índice de la subclave. Este parámetro debe ser cero para la primera llamada y, a continuación, se incrementa en llamadas posteriores  
  
 *pszName*  
 Puntero a un búfer que recibe el nombre de la subclave, incluido el carácter nulo final. Solo el nombre de la subclave que se copia en el búfer, no la jerarquía de claves completo.  
  
 *pnNameLength*  
 Puntero a una variable que especifica el tamaño, en TCHARs, del búfer especificado por el *pszName* parámetro. Este tamaño debe incluir el carácter nulo de terminación. Cuando se devuelve el método, la variable apunta *pnNameLength* contiene el número de caracteres almacenados en el búfer. El recuento devuelto no incluye el carácter nulo de terminación.  
  
 *pftLastWriteTime*  
 Puntero a una variable que recibe el tiempo de la subclave enumerada se escribió por última.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para enumerar las subclaves, llame `CRegKey::EnumKey` con un índice de cero. Incremente el valor de índice y repita hasta que el método devuelve ERROR_NO_MORE_ITEMS. Para obtener más información, consulte [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) en el SDK de Windows.  
  
##  <a name="flush"></a>  CRegKey::Flush  
 Llame a este método para escribir todos los atributos de la clave del registro abierta en el registro.  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) en el SDK de Windows.  
  
##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity  
 Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *Si*  
 El [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) valor que indica la información de seguridad solicitado.  
  
 *PSD*  
 Un puntero a un búfer que recibe una copia del descriptor de seguridad solicitado.  
  
 *pnBytes*  
 El tamaño, en bytes, del búfer señalado por *psd*.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es que un código de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity).  
  
##  <a name="m_hkey"></a>  CRegKey::m_hKey  
 Contiene un identificador de la clave del registro asociada con el `CRegKey` objeto.  
  
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
 Este método notifica al llamador sobre los cambios en los atributos o contenido de la clave del registro abierta.  
  
```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *bWatchSubtree*  
 Especifica una marca que indica si se deben notificar los cambios en la clave especificada y todas sus subclaves o solo en la clave especificada. Si este parámetro es TRUE, el método informa de los cambios en la clave y sus subclaves. Si el parámetro es FALSE, el método informa de los cambios sólo en la clave.  
  
 *dwNotifyFilter*  
 Especifica un conjunto de marcas que controlan los cambios que se debe notificar. Este parámetro puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|Notificar al llamador si se agrega o elimina una subclave.|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|Notificar al llamador de los cambios en los atributos de la clave, como la información del descriptor de seguridad.|  
|REG_NOTIFY_CHANGE_LAST_SET|Notificar al llamador los cambios en un valor de la clave. Esto puede incluir agregar o eliminar un valor o cambiar un valor existente.|  
|REG_NOTIFY_CHANGE_SECURITY|Notificar al llamador de los cambios en el descriptor de seguridad de la clave.|  
  
 *hEvent*  
 Identificador para un evento. Si el *bAsync* parámetro es TRUE, el método devuelve inmediatamente y se notifican los cambios por este evento de señalización. Si *bAsync* es FALSE, *hEvent* se omite.  
  
 *bAsync*  
 Especifica una marca que indica cómo el método informa de los cambios. Si este parámetro es TRUE, el método devuelve inmediatamente e informa de los cambios al señalar el evento especificado. Si este parámetro es FALSE, el método no devuelve hasta que se ha producido un cambio. Si *hEvent* no especifica un evento válido, el *bAsync* parámetro no puede ser TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Este método no notificar al llamador si se elimina la clave especificada.  
  
 Para obtener más detalles y un programa de ejemplo, vea [RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue).  
  
##  <a name="open"></a>  CRegKey::Open  
 Llame a este método para abrir la clave especificada y establece [m_hKey](#m_hkey) al identificador de esta clave.  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *hKeyParent*  
 El identificador de una clave abierta.  
  
 *lpszKeyName*  
 Especifica el nombre de una clave que se creó o se abran. Este nombre debe ser una subclave de *hKeyParent*.  
  
 *samDesired*  
 El acceso de seguridad para la clave. El valor predeterminado es KEY_ALL_ACCESS. Para obtener una lista de posibles valores y descripciones, consulte [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, se define un valor de error distinto de cero en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Si el *lpszKeyName* parámetro es NULL o puntos en una cadena vacía, `Open` abre un nuevo identificador de la clave identificada por *hKeyParent*, pero no cierra ningún identificador abierto anteriormente.  
  
 A diferencia de [CRegKey::Create](#create), `Open` no creará la clave especificada si no existe.  
  
##  <a name="operator_hkey"></a>  CRegKey::operator HKEY  
 Convierte un `CRegKey` objeto a un HKEY.  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>  CRegKey::operator =  
 Operador de asignación.  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *key*  
 Para copiar la clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la nueva clave.  
  
### <a name="remarks"></a>Comentarios  
 Este operador se desasocia *clave* desde su objeto actual y lo asigna a la `CRegKey` objeto en su lugar.  
  
##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue  
 Llame a este método para recuperar los datos binarios de un nombre de valor especificado.  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *pValue*  
 Puntero a un búfer que recibe los datos del valor.  
  
 *pnBytes*  
 Puntero a una variable que especifica el tamaño, en bytes, del búfer señalado por el *pValue* parámetro. Cuando el método vuelve, esta variable contiene el tamaño de los datos copiados en el búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_BINARY, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, el [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) función utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue  
 Llame a este método para recuperar los datos DWORD para un nombre de valor especificado.  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *dwValue*  
 Puntero a un búfer que recibe el valor DWORD.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_DWORD, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, el [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) función utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue  
 Llame a este método para recuperar los datos GUID para un nombre de valor especificado.  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *guidValue*  
 Puntero a una variable que recibe el GUID.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son un GUID válido, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `CRegKey::QueryStringValue` y convierte la cadena en un GUID mediante [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring).  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza.  
  
##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue  
 Llame a este método para recuperar los datos multistring para un nombre de valor especificado.  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *pszValue*  
 Puntero a un búfer que recibe los datos multistring. Una cadena múltiple es una matriz de cadenas terminadas en null, finalizada con dos caracteres null.  
  
 *pnChars*  
 El tamaño, en TCHARs, del búfer señalado por *pszValue*. Cuando el método vuelve, *pnChars* contiene el tamaño, en TCHARs del elemento multistring recuperado, incluido un carácter nulo final.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_MULTI_SZ, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, el [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) función utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue  
 Llame a este método para recuperar los datos de tipo QWORD para un nombre de valor especificado.  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *qwValue*  
 Puntero a un búfer que recibe el QWORD.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_QWORD, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, el [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) función utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue  
 Llame a este método para recuperar los datos de cadena de un nombre de valor especificado.  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 *pszValue*  
 Puntero a un búfer que recibe los datos de cadena.  
  
 *pnChars*  
 El tamaño, en TCHARs, del búfer señalado por *pszValue*. Cuando el método vuelve, *pnChars* contiene el tamaño, en TCHARs, de la cadena recuperado, incluido un carácter nulo final.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_SZ, se devuelve ERROR_INVALID_DATA. Si el método devuelve ERROR_MORE_DATA, *pnChars* es igual a cero, no el tamaño de búfer necesario en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `RegQueryValueEx` y confirma que se devuelve el tipo de datos correcto. Consulte [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, el [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) función utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
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
 *pszValueName*  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta. Si *pszValueName* es NULL o una cadena vacía, "", el método recupera el tipo y datos de la clave sin nombre o valor predeterminado si la hubiera.  
  
 *pdwType*  
 Puntero a una variable que recibe un código que indica el tipo de datos almacenados en el valor especificado. El *pdwType* parámetro puede ser NULL si no se requiere el código de tipo.  
  
 *pData*  
 Puntero a un búfer que recibe los datos del valor. Este parámetro puede ser NULL si no se requieren los datos.  
  
 *pnBytes*  
 Puntero a una variable que especifica el tamaño, en bytes, del búfer señalado por el *pData* parámetro. Cuando el método vuelve, esta variable contiene el tamaño de los datos copiados a *pData.*  
  
 *dwValue*  
 Datos numéricos del campo de valor.  
  
 *lpszValueName*  
 Especifica el campo de valor que se puede consultar.  
  
 *szValue*  
 Datos de cadena del campo de valor.  
  
 *pdwCount*  
 El tamaño de los datos de cadena. Su valor se establece inicialmente en el tamaño de la *szValue* búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Las dos versiones originales de `QueryValue` ya no se admiten y se marcan como ATL_DEPRECATED. El compilador emitirá una advertencia si se usan estos formatos.  
  
 Las llamadas de método restantes RegQueryValueEx.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, posiblemente se están leyendo los datos que no son de confianza. Además, la función de error de RegQueryValueEx utilizada por este método no controla explícitamente las cadenas que son terminado en NULL. Ambas condiciones se deben comprobar el código de llamada.  
  
##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey  
 Llame a este método para quitar la clave especificada del registro y quitar explícitamente todas las subclaves.  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszKey*  
 Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, se define un valor de error distinto de cero en el archivo WINERROR. H.  
  
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
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *pValue*  
 Puntero a un búfer que contiene los datos que se almacenará con el nombre del valor especificado.  
  
 *nBytes*  
 Especifica el tamaño, en bytes, de la información que apunta el *pValue* parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) para escribir el valor en el registro.  
  
##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue  
 Llame a este método para establecer el valor DWORD de la clave del registro.  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *dwValue*  
 Los datos DWORD que se almacena con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) para escribir el valor en el registro.  
  
##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue  
 Llame a este método para establecer el valor GUID de la clave del registro.  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *guidValue*  
 Referencia a lo GUID que se almacenará con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `CRegKey::SetStringValue` y convierte el GUID en una cadena con [StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2).  
  
##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue  
 Llame a este método para almacenar datos en un campo de valor especificado de una clave especificada.  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszKeyName*  
 Especifica el nombre de la clave que se crea o se abre. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
 *lpszValue*  
 Especifica los datos que se almacenará. Este parámetro debe ser distinto de NULL.  
  
 *lpszValueName*  
 Especifica el campo de valor debe establecerse. Si un campo de valor con este nombre no existe en la clave, se agrega.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para crear o abrir el *lpszKeyName* clave y almacenar el *lpszValue* datos en el *lpszValueName* campo de valor.  
  
##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity  
 Llame a este método para establecer la seguridad de la clave del registro.  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *Si*  
 Especifica los componentes del descriptor de seguridad para establecer. El valor puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|Establece la lista de la clave control de acceso discrecional (DACL). La clave debe tener acceso WRITE_DAC o el proceso de llamada debe ser el propietario del objeto.|  
|GROUP_SECURITY_INFORMATION|Establece el identificador de la clave principal del grupo seguridad (SID). La clave debe tener acceso WRITE_OWNER o el proceso de llamada debe ser el propietario del objeto.|  
|OWNER_SECURITY_INFORMATION|Establece el propietario de la clave SID. La clave debe tener acceso WRITE_OWNER o el proceso de llamada debe ser el propietario del objeto o tener el privilegio SE_TAKE_OWNERSHIP_NAME habilitado.|  
|SACL_SECURITY_INFORMATION|Establece la lista de control de acceso de la clave del sistema (SACL). La clave debe tener acceso ACCESS_SYSTEM_SECURITY. La manera adecuada de obtener este acceso es habilitar el SE_SECURITY_NAME [privilegio](https://msdn.microsoft.com/library/windows/desktop/aa379306) en el token de acceso actual del llamador, abrir el identificador para el acceso ACCESS_SYSTEM_SECURITY y, a continuación, deshabilite el privilegio.|  
  
 *PSD*  
 Puntero a un [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) estructura que especifica los atributos de seguridad para establecer la clave especificada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Establece los atributos de seguridad de la clave. Consulte [RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) para obtener más detalles.  
  
##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue  
 Llame a este método para establecer el valor multistring de la clave del registro.  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *pszValue*  
 Puntero a los datos multistring almacenarse con el nombre del valor especificado. Una cadena múltiple es una matriz de cadenas terminadas en null, finalizada con dos caracteres null.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) para escribir el valor en el registro.  
  
##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue  
 Llame a este método para establecer el valor QWORD de la clave del registro.  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *qwValue*  
 Los datos de tipo QWORD almacenarse con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) para escribir el valor en el registro.  
  
##  <a name="setstringvalue"></a>  CRegKey::SetStringValue  
 Llame a este método para establecer el valor de cadena de la clave del registro.  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente, el método lo agrega a la clave.  
  
 *pszValue*  
 Puntero a los datos de cadena que se almacenará con el nombre del valor especificado.  
  
 *dwType*  
 El tipo de cadena que se escribirá en el registro: REG_SZ (valor predeterminado) o REG_EXPAND_SZ (para multistrings).  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) para escribir el valor en el registro.  
  
##  <a name="setvalue"></a>  CRegKey::SetValue  
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
 *pszValueName*  
 Puntero a una cadena que contiene el nombre del valor para establecer. Si un valor con este nombre ya no está presente en la clave, el método lo agrega a la clave. Si *pszValueName* es NULL o una cadena vacía, "", el método establece el tipo y sin nombre de la información de la clave o el valor predeterminado.  
  
 *dwType*  
 Especifica un código que indica el tipo de datos que apunta el *pValue* parámetro.  
  
 *pValue*  
 Puntero a un búfer que contiene los datos que se almacenará con el nombre del valor especificado.  
  
 *nBytes*  
 Especifica el tamaño, en bytes, de la información que apunta el *pValue* parámetro. Si los datos están de tipo REG_SZ, REG_EXPAND_SZ o REG_MULTI_SZ, *nBytes* debe incluir el tamaño del carácter nulo de terminación.  
  
 *hKeyParent*  
 El identificador de una clave abierta.  
  
 *lpszKeyName*  
 Especifica el nombre de una clave que se creó o se abran. Este nombre debe ser una subclave de *hKeyParent*.  
  
 *lpszValue*  
 Especifica los datos que se almacenará. Este parámetro debe ser distinto de NULL.  
  
 *lpszValueName*  
 Especifica el campo de valor debe establecerse. Si un campo de valor con este nombre no existe en la clave, se agrega.  
  
 *dwValue*  
 Especifica los datos que se almacenará.  
  
 *bMulti*  
 Si es false, indica que la cadena es de tipo REG_SZ. Si es true, indica que la cadena es una cadena múltiple del tipo REG_MULTI_SZ.  
  
 *nValueLen*  
 Si *bMulti* es true, *nValueLen* es la longitud de la *lpszValue* cadena en caracteres. Si *bMulti* es false, el valor -1 indica que el método calculará automáticamente la longitud.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Las dos versiones originales de `SetValue` se marcan como ATL_DEPRECATED y ya no se debe usar. El compilador emitirá una advertencia si se usan estos formatos.  
  
 El tercer método llama a [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo DCOM](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
