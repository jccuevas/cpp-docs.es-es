---
title: Clase CRegKey | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dffc650c54c4a50fb4b3b1fe2c22ac82501b8b45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cregkey-class"></a>Clase CRegKey
Esta clase proporciona métodos para manipular las entradas en el registro del sistema.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
|[CRegKey::Attach](#attach)|Llamar a este método para asociar un HKEY que se va a la `CRegKey` objeto estableciendo la [m_hKey](#m_hkey) identificador de miembro `hKey`.|  
|[CRegKey::Close](#close)|Llamar a este método para liberar la [m_hKey](#m_hkey) miembro controlar y establece en NULL.|  
|[CRegKey::Create](#create)|Llamar a este método para crear la clave especificada, si no existe como una subclave de `hKeyParent`.|  
|[CRegKey::DeleteSubKey](#deletesubkey)|Llame a este método para quitar la clave especificada del registro.|  
|[CRegKey::DeleteValue](#deletevalue)|Llamar a este método para quitar un campo de valor de [m_hKey](#m_hkey).|  
|[CRegKey::Detach](#detach)|Llamar a este método para separar el [m_hKey](#m_hkey) identificador de miembro de la `CRegKey` de objeto y establecer `m_hKey` en NULL.|  
|[CRegKey::EnumKey](#enumkey)|Llame a este método para enumerar las subclaves de la clave del registro abierta.|  
|[CRegKey::Flush](#flush)|Llamar a este método para escribir todos los atributos de la clave del registro abierta y en el registro.|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|Llamar a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Este método notifica al llamador sobre los cambios en los atributos o contenido de la clave del registro abierta.|  
|[CRegKey::Open](#open)|Llamar a este método para abrir la clave especificada y establece [m_hKey](#m_hkey) al identificador de esta clave.|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Llamar a este método para recuperar los datos binarios de un nombre de valor especificado.|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Llamar a este método para recuperar los datos DWORD para un nombre de valor especificado.|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Llamar a este método para recuperar los datos GUID para un nombre de valor especificado.|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Llamar a este método para recuperar los datos multistring para un nombre de valor especificado.|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Llamar a este método para recuperar los datos de tipo QWORD para un nombre de valor especificado.|  
|[CRegKey::QueryStringValue](#querystringvalue)|Llamar a este método para recuperar los datos de cadena de un nombre de valor especificado.|  
|[CRegKey::QueryValue](#queryvalue)|Llamar a este método para recuperar los datos para el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como **ATL_DEPRECATED**.|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Llame a este método para quitar la clave especificada del registro y quitar explícitamente todas las subclaves.|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Llame a este método para establecer el valor binario de la clave del registro.|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|Llame a este método para establecer el valor DWORD de la clave del registro.|  
|[CRegKey::SetGUIDValue](#setguidvalue)|Llamar a este método para establecer el valor GUID de la clave del registro.|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|Llame a este método para establecer la seguridad de la clave del registro.|  
|[CRegKey::SetKeyValue](#setkeyvalue)|Llamar a este método para almacenar datos en un campo de valor especificado de una clave especificada.|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Llamar a este método para establecer el valor de la clave del registro multistring.|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|Llamar a este método para establecer el valor QWORD de la clave del registro.|  
|[CRegKey::SetStringValue](#setstringvalue)|Llame a este método para establecer el valor de cadena de la clave del registro.|  
|[CRegKey::SetValue](#setvalue)|Llamar a este método para almacenar datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como **ATL_DEPRECATED**.|  
  
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
 `CRegKey`Proporciona métodos para crear y eliminar claves y valores en el registro del sistema. El registro contiene un conjunto de definiciones para los componentes del sistema, como números de versión de software, asignaciones de lógica física de hardware que haya instalado y objetos COM específicos de instalación.  
  
 `CRegKey`Proporciona una interfaz de programación para el registro del sistema para un equipo determinado. Por ejemplo, para abrir una clave del Registro determinada, llame a `CRegKey::Open`. Para recuperar o modificar un valor de datos, llame a `CRegKey::QueryValue` o `CRegKey::SetValue`, respectivamente. Para cerrar una clave, llame a `CRegKey::Close`.  
  
 Al cerrar una clave, sus datos de registro se escriben (vaciado) en el disco duro. Este proceso puede tardar varios segundos. Si la aplicación debe escribir explícitamente los datos del registro en el disco duro, puede llamar a la [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) función de Win32. Sin embargo, **RegFlushKey** usa muchos recursos del sistema y se debe llamar solo cuando sea absolutamente necesario.  
  
> [!IMPORTANT]
>  Los métodos que permiten el llamador especificar una ubicación del registro tienen el potencial para leer datos que no son de confianza. Métodos que hacen usan de [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) debe tener en cuenta que esta función no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="attach"></a>CRegKey::Attach  
 Llamar a este método para asociar un HKEY que se va a la `CRegKey` objeto estableciendo la [m_hKey](#m_hkey) identificador de miembro `hKey`.  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 El identificador de una clave del registro.  
  
### <a name="remarks"></a>Comentarios  
 **Adjuntar** impondrá si `m_hKey` es distinto de NULL.  
  
##  <a name="close"></a>CRegKey::Close  
 Llamar a este método para liberar la [m_hKey](#m_hkey) miembro controlar y establece en NULL.  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; de lo contrario, devuelve un valor de error.  
  
##  <a name="create"></a>CRegKey::Create  
 Llamar a este método para crear la clave especificada, si no existe como una subclave de `hKeyParent`.  
  
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
 `hKeyParent`  
 El identificador de una clave abierta.  
  
 `lpszKeyName`  
 Especifica el nombre de una clave para crear o abrir. Este nombre debe ser una subclave de `hKeyParent`.  
  
 `lpszClass`  
 Especifica la clase de la clave para crear o abrir. El valor predeterminado es REG_NONE.  
  
 `dwOptions`  
 Opciones de la clave. El valor predeterminado es REG_OPTION_NON_VOLATILE. Para obtener una lista de valores posibles y descripciones, consulte [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) del SDK de Windows.  
  
 `samDesired`  
 El acceso de seguridad para la clave. El valor predeterminado es KEY_READ &#124; KEY_WRITE. Para obtener una lista de valores posibles y descripciones, consulte **RegCreateKeyEx**.  
  
 *lpSecAttr*  
 Un puntero a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que indica si un proceso secundario puede heredar el identificador de la clave. De forma predeterminada, este parámetro es NULL (es decir, no se puede heredar el identificador).  
  
 *lpdwDisposition*  
 [out] Si no es NULL, recupera REG_CREATED_NEW_KEY (si la clave no existía y se ha creado) o REG_OPENED_EXISTING_KEY (si la clave existía y se abrió).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS y abre la clave. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** establece la [m_hKey](#m_hkey) miembro para el identificador de esta clave.  
  
##  <a name="cregkey"></a>CRegKey::CRegKey  
 El constructor.  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Referencia a un objeto `CRegKey`.  
  
 `hKey`  
 Un identificador para una clave del registro.  
  
 `pTM`  
 Puntero al objeto CAtlTransactionManager  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo objeto `CRegKey`. El objeto se puede crear desde una existente `CRegKey` objeto, o desde un identificador de una clave del registro.  
  
##  <a name="dtor"></a>CRegKey:: ~ CRegKey  
 Destructor.  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Las versiones de destructor `m_hKey`.  
  
##  <a name="deletesubkey"></a>CRegKey::DeleteSubKey  
 Llame a este método para quitar la clave especificada del registro.  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSubKey`  
 Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 `DeleteSubKey`solo se puede eliminar una clave que tenga subclaves. Si la clave tiene subclaves, llame a [RecurseDeleteKey](#recursedeletekey) en su lugar.  
  
##  <a name="deletevalue"></a>CRegKey::DeleteValue  
 Llamar a este método para quitar un campo de valor de [m_hKey](#m_hkey).  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszValue`  
 Especifica el campo de valor para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
##  <a name="detach"></a>CRegKey::Detach  
 Llamar a este método para separar el [m_hKey](#m_hkey) identificador de miembro de la `CRegKey` de objeto y establecer `m_hKey` en NULL.  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 HKEY que se va asociado a la `CRegKey` objeto.  
  
##  <a name="enumkey"></a>CRegKey::EnumKey  
 Llame a este método para enumerar las subclaves de la clave del registro abierta.  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iIndex`  
 El índice de la subclave. Este parámetro debe ser cero para la primera llamada y, a continuación, se incrementa para llamadas posteriores  
  
 `pszName`  
 Puntero a un búfer que recibe el nombre de la subclave, incluido el carácter nulo final. Solo el nombre de la subclave que se copia en el búfer, no la jerarquía de claves completo.  
  
 *pnNameLength*  
 Puntero a una variable que especifica el tamaño, en TCHARs, del búfer especificado por el `pszName` parámetro. Este tamaño debe incluir el carácter nulo de terminación. Cuando se devuelve el método, la variable que señala *pnNameLength* contiene el número de caracteres almacenados en el búfer. El recuento devuelto no incluye el carácter nulo de terminación.  
  
 *pftLastWriteTime*  
 Puntero a una variable que recibe la hora de la subclave enumerada se escribió por última.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para enumerar las subclaves, llamar a `CRegKey::EnumKey` con un índice de cero. Incrementar el valor de índice y repita hasta que el método devuelve ERROR_NO_MORE_ITEMS. Para obtener más información, consulte [en RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862) del SDK de Windows.  
  
##  <a name="flush"></a>CRegKey::Flush  
 Llamar a este método para escribir todos los atributos de la clave del registro abierta y en el registro.  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867) en el SDK de Windows.  
  
##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity  
 Llamar a este método para recuperar una copia del descriptor de seguridad que protege la clave del registro abierta.  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `si`  
 El [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) valor que indica la información de seguridad solicitada.  
  
 `psd`  
 Un puntero a un búfer que recibe una copia del descriptor de seguridad solicitado.  
  
 `pnBytes`  
 El tamaño, en bytes, del búfer señalado por `psd`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es que un código de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313).  
  
##  <a name="m_hkey"></a>CRegKey::m_hKey  
 Contiene un identificador de la clave del registro asociada con el `CRegKey` objeto.  
  
```
HKEY m_hKey;
```  
  
##  <a name="m_ptm"></a>CRegKey::m_pTM  
 Puntero a un `CAtlTransactionManager` objeto.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue  
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
 Especifica una marca que indica si se notifican los cambios en la clave especificada y todas sus subclaves o solo en la clave especificada. Si este parámetro es TRUE, el método notifica los cambios en la clave y sus subclaves. Si el parámetro es FALSE, el método notifica los cambios únicamente en la clave.  
  
 *dwNotifyFilter*  
 Especifica un conjunto de marcas que controlan los cambios que se debería notificar. Este parámetro puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|Notificar al llamador si se agrega o elimina una subclave.|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|Notificar al llamador de los cambios en los atributos de la clave, como la información del descriptor de seguridad.|  
|REG_NOTIFY_CHANGE_LAST_SET|Notificar al llamador de los cambios en un valor de la clave. Esto puede incluir la adición o eliminación de un valor o cambiar un valor existente.|  
|REG_NOTIFY_CHANGE_SECURITY|Notificar al llamador de los cambios en el descriptor de seguridad de la clave.|  
  
 `hEvent`  
 Identificador para un evento. Si el *bAsync* parámetro es TRUE, el método vuelve inmediatamente y se notifican los cambios mediante señales este evento. Si `bAsync` es FALSE, `hEvent` se omite.  
  
 `bAsync`  
 Especifica una marca que indica cómo el método notifica los cambios. Si este parámetro es TRUE, el método vuelve inmediatamente e informa de los cambios al señalar el evento especificado. Si este parámetro es FALSE, el método no devuelve hasta que se ha producido un cambio. Si `hEvent` no especifica un evento válido, el `bAsync` parámetro no puede ser TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Este método no notificar al llamador si se elimina la clave especificada.  
  
 Para obtener más detalles y un programa de ejemplo, vea [RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892).  
  
##  <a name="open"></a>CRegKey::Open  
 Llamar a este método para abrir la clave especificada y establece [m_hKey](#m_hkey) al identificador de esta clave.  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hKeyParent`  
 El identificador de una clave abierta.  
  
 `lpszKeyName`  
 Especifica el nombre de una clave para crear o abrir. Este nombre debe ser una subclave de `hKeyParent`.  
  
 `samDesired`  
 El acceso de seguridad para la clave. El valor predeterminado es KEY_ALL_ACCESS. Para obtener una lista de valores posibles y descripciones, consulte [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) del SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un valor de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Si el `lpszKeyName` parámetro es NULL o puntos en una cadena vacía, **abiertos** abre un nuevo identificador de la clave identificada por `hKeyParent`, pero no cierra cualquier identificador abierto anteriormente.  
  
 A diferencia de [CRegKey::Create](#create), **abiertos** no creará la clave especificada si no existe.  
  
##  <a name="operator_hkey"></a>CRegKey::operator HKEY  
 Convierte un `CRegKey` objeto a un HKEY.  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>CRegKey::operator =  
 Operador de asignación.  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave que se va a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la nueva clave.  
  
### <a name="remarks"></a>Comentarios  
 Este operador se desasocia `key` de su objeto actual y lo asigna a la `CRegKey` objeto en su lugar.  
  
##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue  
 Llamar a este método para recuperar los datos binarios de un nombre de valor especificado.  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `pValue`  
 Puntero a un búfer que recibe los datos del valor.  
  
 `pnBytes`  
 Puntero a una variable que especifica el tamaño, en bytes, del búfer que señala el `pValue` parámetro. Cuando el método vuelve, esta variable contiene el tamaño de los datos copiados en el búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_BINARY, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de **error de RegQueryValueEx** y confirma que se devuelve el tipo de datos correcto. Vea [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, el [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) función utilizada por este método no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue  
 Llamar a este método para recuperar los datos DWORD para un nombre de valor especificado.  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `dwValue`  
 Puntero a un búfer que recibe el valor DWORD.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_DWORD, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de **error de RegQueryValueEx** y confirma que se devuelve el tipo de datos correcto. Vea [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, el [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) función utilizada por este método no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue  
 Llamar a este método para recuperar los datos GUID para un nombre de valor especificado.  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `guidValue`  
 Puntero a una variable que recibe el GUID.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son un GUID válido, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `CRegKey::QueryStringValue` y convierte la cadena en un GUID mediante [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589).  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza.  
  
##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue  
 Llamar a este método para recuperar los datos multistring para un nombre de valor especificado.  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `pszValue`  
 Puntero a un búfer que recibe los datos multistring. Un multistring es una matriz de cadenas terminadas en null, finalizada con dos caracteres null.  
  
 `pnChars`  
 El tamaño, en TCHARs, del búfer señalado por `pszValue`. Cuando el método vuelve, `pnChars` contiene el tamaño, en TCHARs, de la multistring recuperado, incluido un carácter nulo final.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_MULTI_SZ, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de **error de RegQueryValueEx** y confirma que se devuelve el tipo de datos correcto. Vea [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, el [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) función utilizada por este método no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue  
 Llamar a este método para recuperar los datos de tipo QWORD para un nombre de valor especificado.  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `qwValue`  
 Puntero a un búfer que recibe la QWORD.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son de tipo REG_QWORD, se devuelve ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de **error de RegQueryValueEx** y confirma que se devuelve el tipo de datos correcto. Vea [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, el [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) función utilizada por este método no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="querystringvalue"></a>CRegKey::QueryStringValue  
 Llamar a este método para recuperar los datos de cadena de un nombre de valor especificado.  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta.  
  
 `pszValue`  
 Puntero a un búfer que recibe los datos de cadena.  
  
 `pnChars`  
 El tamaño, en TCHARs, del búfer señalado por `pszValue`. Cuando el método vuelve, `pnChars` contiene el tamaño, en TCHARs, de la cadena que se recuperan, incluido un carácter nulo final.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, se devuelve ERROR_SUCCESS. Si el método no puede leer un valor, devuelve un código de error distinto de cero definido en el archivo WINERROR. H. Si los datos al que hace referencia no son del tipo REG_SZ, se devuelve ERROR_INVALID_DATA. Si el método devuelve ERROR_MORE_DATA, `pnChars` es igual a cero, no el tamaño de búfer necesario en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de **error de RegQueryValueEx** y confirma que se devuelve el tipo de datos correcto. Vea [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) para obtener más detalles.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, el [error de RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) función utilizada por este método no controlar explícitamente las cadenas que son terminadas en NULL. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="queryvalue"></a>CRegKey::QueryValue  
 Llamar a este método para recuperar los datos para el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como **ATL_DEPRECATED**.  
  
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
 `pszValueName`  
 Puntero a una cadena terminada en null que contiene el nombre del valor a la consulta. Si `pszValueName` es NULL o una cadena vacía, "", el método recupera el tipo y datos de la clave del nombre o valor predeterminado si la hubiera.  
  
 `pdwType`  
 Puntero a una variable que recibe un código que indica el tipo de datos almacenados en el valor especificado. El `pdwType` parámetro puede ser NULL si no se requiere el código de tipo.  
  
 `pData`  
 Puntero a un búfer que recibe los datos del valor. Este parámetro puede ser NULL si no se requieren los datos.  
  
 `pnBytes`  
 Puntero a una variable que especifica el tamaño, en bytes, del búfer que señala el `pData` parámetro. Cuando el método vuelve, esta variable contiene el tamaño de los datos copiados a *pData.*  
  
 `dwValue`  
 Datos numéricos del campo de valor.  
  
 `lpszValueName`  
 Especifica el campo de valor desea consultar.  
  
 `szValue`  
 Datos de cadena del campo de valor.  
  
 `pdwCount`  
 El tamaño de los datos de cadena. Su valor está establecido inicialmente en el tamaño de la `szValue` búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Las dos versiones originales de `QueryValue` ya no se admiten y se marcan como **ATL_DEPRECATED**. El compilador emitirá una advertencia si se utilizan estas formas.  
  
 Las llamadas de método restantes RegQueryValueEx.  
  
> [!IMPORTANT]
>  Este método permite al llamador especificar cualquier ubicación del registro, podría leer los datos que no son de confianza. Además, la función de error de RegQueryValueEx utilizada por este método no controlar explícitamente las cadenas que son `NULL` terminada. Ambas condiciones se deben comprobar el código que llama.  
  
##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey  
 Llame a este método para quitar la clave especificada del registro y quitar explícitamente todas las subclaves.  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszKey*  
 Especifica el nombre de la clave que se va a eliminar. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un valor de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Si la clave tiene subclaves, debe llamar a este método para eliminar la clave.  
  
##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue  
 Llame a este método para establecer el valor binario de la clave del registro.  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `pValue`  
 Puntero a un búfer que contiene los datos que se almacenará con el nombre del valor especificado.  
  
 `nBytes`  
 Especifica el tamaño, en bytes, de la información que señala el `pValue` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) para escribir el valor en el registro.  
  
##  <a name="setdwordvalue"></a>CRegKey::SetDWORDValue  
 Llame a este método para establecer el valor DWORD de la clave del registro.  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `dwValue`  
 Los datos DWORD que se almacenará con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) para escribir el valor en el registro.  
  
##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue  
 Llamar a este método para establecer el valor GUID de la clave del registro.  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `guidValue`  
 Referencia a lo GUID que se almacenará con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace uso de `CRegKey::SetStringValue` y convierte el GUID en una cadena con [StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893).  
  
##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue  
 Llamar a este método para almacenar datos en un campo de valor especificado de una clave especificada.  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszKeyName`  
 Especifica el nombre de la clave para crear o abrir. Este nombre debe ser una subclave de [m_hKey](#m_hkey).  
  
 `lpszValue`  
 Especifica los datos que se va a almacenar. Este parámetro debe ser distinto de NULL.  
  
 `lpszValueName`  
 Especifica el campo de valor se establezca. Si un campo de valor con este nombre no existe en la clave, se agrega.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para crear o abrir el `lpszKeyName` clave y almacenar el `lpszValue` datos en el `lpszValueName` campo de valor.  
  
##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity  
 Llame a este método para establecer la seguridad de la clave del registro.  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `si`  
 Especifica los componentes del descriptor de seguridad para establecer. El valor puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|Establece la lista de la clave control de acceso discrecional (DACL). La clave debe tener acceso WRITE_DAC o el proceso que realiza la llamada debe ser el propietario del objeto.|  
|GROUP_SECURITY_INFORMATION|Establece el identificador de seguridad de la clave principal de grupo (SID). La clave debe tener acceso WRITE_OWNER o el proceso que realiza la llamada debe ser el propietario del objeto.|  
|OWNER_SECURITY_INFORMATION|Establece el propietario de la clave SID. La clave debe tener acceso WRITE_OWNER o el proceso que realiza la llamada debe ser el propietario del objeto o tener el privilegio SE_TAKE_OWNERSHIP_NAME habilitado.|  
|SACL_SECURITY_INFORMATION|Establece la lista de control de acceso de la clave sistema (SACL). La clave debe tener acceso ACCESS_SYSTEM_SECURITY. La manera adecuada de obtener este acceso es habilitar el SE_SECURITY_NAME [privilegios](http://msdn.microsoft.com/library/windows/desktop/aa379306) en el token de acceso actual del llamador, abrir el identificador para el acceso ACCESS_SYSTEM_SECURITY y, a continuación, deshabilite el privilegio.|  
  
 `psd`  
 Puntero a un [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) estructura que especifica los atributos de seguridad para establecer la clave especificada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Establece los atributos de seguridad de la clave. Vea [RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314) para obtener más detalles.  
  
##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue  
 Llamar a este método para establecer el valor de la clave del registro multistring.  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `pszValue`  
 Puntero a los datos multistring almacenarse con el nombre del valor especificado. Un multistring es una matriz de cadenas terminadas en null, finalizada con dos caracteres null.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) para escribir el valor en el registro.  
  
##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue  
 Llamar a este método para establecer el valor QWORD de la clave del registro.  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `qwValue`  
 Los datos de tipo QWORD almacenarse con el nombre del valor especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) para escribir el valor en el registro.  
  
##  <a name="setstringvalue"></a>CRegKey::SetStringValue  
 Llame a este método para establecer el valor de cadena de la clave del registro.  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente, el método agrega a la clave.  
  
 `pszValue`  
 Puntero a los datos de cadena que se almacenará con el nombre del valor especificado.  
  
 `dwType`  
 El tipo de cadena que se escribirá en el registro: (valor predeterminado) de REG_SZ o REG_EXPAND_SZ (para elementos MultiString).  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método tiene éxito, el valor devuelto es ERROR_SUCCESS. Si se produce un error en el método, el valor devuelto es un código de error distinto de cero definido en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx) para escribir el valor en el registro.  
  
##  <a name="setvalue"></a>CRegKey::SetValue  
 Llamar a este método para almacenar datos en el campo de valor especificado de [m_hKey](#m_hkey). Las versiones anteriores de este método ya no se admiten y se marcan como **ATL_DEPRECATED**.  
  
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
 `pszValueName`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer. Si un valor con este nombre ya no está presente en la clave, el método agrega a la clave. Si `pszValueName` es NULL o una cadena vacía, "", el método establece el tipo y datos de la clave del nombre o valor predeterminado.  
  
 `dwType`  
 Especifica un código que indica el tipo de datos que señala el `pValue` parámetro.  
  
 `pValue`  
 Puntero a un búfer que contiene los datos que se almacenará con el nombre del valor especificado.  
  
 `nBytes`  
 Especifica el tamaño, en bytes, de la información que señala el `pValue` parámetro. Si los datos son de tipo REG_SZ, REG_EXPAND_SZ o REG_MULTI_SZ, `nBytes` debe incluir el tamaño del carácter nulo de terminación.  
  
 `hKeyParent`  
 El identificador de una clave abierta.  
  
 `lpszKeyName`  
 Especifica el nombre de una clave para crear o abrir. Este nombre debe ser una subclave de `hKeyParent`.  
  
 `lpszValue`  
 Especifica los datos que se va a almacenar. Este parámetro debe ser distinto de NULL.  
  
 `lpszValueName`  
 Especifica el campo de valor se establezca. Si un campo de valor con este nombre no existe en la clave, se agrega.  
  
 `dwValue`  
 Especifica los datos que se va a almacenar.  
  
 `bMulti`  
 Si es false, indica que la cadena es de tipo REG_SZ. Si es true, indica que la cadena es un multistring de tipo REG_MULTI_SZ.  
  
 `nValueLen`  
 Si `bMulti` es true, `nValueLen` es la longitud de la *lpszValue* cadena en caracteres. Si `bMulti` es false, el valor -1 indica que el método calculará automáticamente la longitud.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve ERROR_SUCCESS; en caso contrario, un código de error distinto de cero se define en el archivo WINERROR. H.  
  
### <a name="remarks"></a>Comentarios  
 Las dos versiones originales de `SetValue` se marcan como **ATL_DEPRECATED** y ya no debe usarse. El compilador emitirá una advertencia si se utilizan estas formas.  
  
 Las llamadas al método tercer [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo DCOM](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
