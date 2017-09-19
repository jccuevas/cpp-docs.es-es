---
title: Clase CSettingsStore | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStore class
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
caps.latest.revision: 29
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0b07f6b12e178d8e324313ea3b0f6de9ae7420c9
ms.openlocfilehash: 0918c8dd9b6284adecb61bc95ddfd41c22d16cb8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
|[CSettingsStore::Close](#close)|Cierra la clave del registro abierta.|  
|[CSettingsStore::CreateKey](#createkey)|Se abre la clave especificada o lo crea si no existe.|  
|[CSettingsStore::DeleteKey](#deletekey)|Elimina la clave especificada y todos sus nodos secundarios.|  
|[CSettingsStore::DeleteValue](#deletevalue)|Elimina el valor especificado de la clave abierta.|  
|[CSettingsStore::Open](#open)|Se abre la clave especificada.|  
|[CSettingsStore::Read](#read)|Recupera los datos de un valor de clave especificado.|  
|[CSettingsStore::Write](#write)|Escribe un valor en el registro bajo la clave abierta.|  
  
## <a name="remarks"></a>Comentarios  
 Las funciones miembro `CreateKey` y `Open` son muy similares. Si ya existe la clave del registro, `CreateKey` y `Open` función de la misma manera. Sin embargo, si la clave del registro no existe, `CreateKey` creará mientras que `Open` devolverá un valor de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar los métodos Open y lectura de la `CSettingsStore` clase. Este fragmento de código forma parte de la [ejemplo de demostración de sugerencia de herramienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_ToolTipDemo](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSettingsStore`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsettingsstore.h  
  
##  <a name="close"></a>CSettingsStore::Close  
 Cierra la clave del registro abierta.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, se llama a este método desde el destructor de la [CSettingsStore clase](../../mfc/reference/csettingsstore-class.md).  
  
##  <a name="createkey"></a>CSettingsStore::CreateKey  
 Se abre una clave del registro o lo crea si no existe.  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszPath`  
 Especifica el nombre de una clave para crear o abrir.  
  
### <a name="return-value"></a>Valor devuelto  
 0 si es correcto; de lo contrario, un valor distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 `CreateKey`utiliza `m_hKey` como la raíz de las consultas del registro. Busca `pszPath` como subclave de `m_hKey`. Si la clave no existe, `CreateKey` lo crea. De lo contrario, abre la clave. `CreateKey`a continuación, se establece `m_hKey` a la clave creada o abierta.  
  
##  <a name="csettingsstore"></a>CSettingsStore::CSettingsStore  
 Crea un objeto `CSettngsStore`.  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAdmin`  
 Parámetro booleano que especifica si la `CSettingsStore` objeto actúa en modo de administrador.  
  
 [in] `bReadOnly`  
 Parámetro booleano que especifica si la `CSettingsStore` objeto se crea en modo de sólo lectura.  
  
### <a name="remarks"></a>Comentarios  
 Si `bAdmin` está establecido en `false`, `m_hKey` variable miembro está establecida en `HKEY_LOCAL_MACHINE`. If you set `bAdmin` to `true`, `m_hKey` is set to `HKEY_CURRENT_USER`.  
  
 El acceso de seguridad depende del `bReadOnly` parámetro. Si `bReadonly` es `false`, el acceso de seguridad se establecerá en `KEY_ALL_ACCESS`. Si `bReadyOnly` es `true`, el acceso de seguridad se establecerá en una combinación de `KEY_QUERY_VALUE, KEY_NOTIFY` y `KEY_ENUMERATE_SUB_KEYS`. Para obtener más información acerca del acceso de seguridad junto con el registro, consulte [derechos de acceso y seguridad de la clave del registro](http://msdn.microsoft.com/library/windows/desktop/ms724878).  
  
 El destructor de `CSettingsStore` libera `m_hKey` automáticamente.  
  
##  <a name="deletekey"></a>CSettingsStore::DeleteKey  
 Elimina una clave y todos sus elementos secundarios del registro.  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszPath`  
 El nombre de la clave que se va a eliminar.  
  
 [in] `bAdmin`  
 Modificador que especifica la ubicación de la clave que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Este método se producirá un error si la `CSettingsStore` objeto está en modo de sólo lectura.  
  
 Si el parámetro `bAdmin` es cero, `DeleteKey` busca la clave eliminar en `HKEY_CURRENT_USER`. Si `bAdmin` es distinto de cero, `DeleteKey` busca la clave eliminar en `HKEY_LOCAL_MACHINE`.  
  
##  <a name="deletevalue"></a>CSettingsStore::DeleteValue  
 Elimina un valor de `m_hKey`.  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszValue`  
 Especifica el campo de valor para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="open"></a>CSettingsStore::Open  
 Se abre una clave del registro.  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszPath`  
 El nombre de una clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Después de que este método abre correctamente la clave especificada, establece `m_hKey` en el identificador de esta clave.  
  
##  <a name="read"></a>CSettingsStore::Read  
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
 [in] `pszKey`  
 Puntero a una cadena terminada en null que contiene el nombre del valor que se va a leer desde el registro.  
  
 [out] `iVal`  
 Referencia a una variable entera que recibe el valor leído de la clave del registro.  
  
 [out] `dwVal`  
 Referencia a una variable de doble palabra de 32 bits que recibe el valor leído de la clave del registro.  
  
 [out] `sVal`  
 Referencia a una variable de cadena que recibe el valor leído de la clave del registro.  
  
 [out] `scStringList`  
 Referencia a una variable de la lista de cadena que recibe el valor leído de la clave del registro.  
  
 [out] `scArray`  
 Referencia a una variable de matriz de cadena que recibe el valor leído de la clave del registro.  
  
 [out] `dwcArray`  
 Referencia a una variable de matriz de doble palabra de 32 bits que recibe el valor leído de la clave del registro.  
  
 [out] `wcArray`  
 Referencia a una variable de matriz de palabras de 16 bits que recibe el valor leído de la clave del registro.  
  
 [out] `bcArray`  
 Referencia a una variable de matriz de bytes que recibe el valor leído de la clave del registro.  
  
 [out] `lpPoint`  
 Referencia a un puntero a un `POINT` estructura que recibe el valor de lee la clave del registro.  
  
 [out] `rect`  
 Hacer referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) variable que recibe el valor leído desde la clave del registro.  
  
 [out] `ppData`  
 Puntero a un puntero a los datos que recibe el valor de lee la clave del registro.  
  
 [out] `pBytes`  
 Puntero a una variable de entero sin signo. Esta variable recibe el tamaño del búfer que `ppData` señala.  
  
 [out] `list`  
 Hacer referencia a un [CObList](../../mfc/reference/coblist-class.md) variable que recibe el valor leído desde la clave del registro.  
  
 [out] `obj`  
 Hacer referencia a un [CObject](../../mfc/reference/cobject-class.md) variable que recibe el valor leído desde la clave del registro.  
  
 [out] `pObj`  
 Referencia a un puntero a un `CObject` variable que recibe el valor leído desde la clave del registro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 `Read`busca `pszKey` como subclave de `m_hKey`.  
  
##  <a name="write"></a>CSettingsStore::Write  
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
 [in] `pszKey`  
 Puntero a una cadena que contiene el nombre del valor que se va a establecer.  
  
 [in] `iVal`  
 Referencia a una variable entera que contiene los datos a almacenar.  
  
 [in] `dwVal`  
 Referencia a una variable de doble palabra de 32 bits que contiene los datos a almacenar.  
  
 [in] `pszVal`  
 Puntero a una variable de cadena terminada en null que contiene los datos a almacenar.  
  
 [in] `scStringList`  
 Hacer referencia a un [objeto CStringList](../../mfc/reference/cstringlist-class.md) variable que contiene los datos a almacenar.  
  
 [in] `bcArray`  
 Referencia a una variable de matriz de bytes que contiene los datos a almacenar.  
  
 [in] `scArray`  
 Referencia a una variable de matriz de cadena que contiene los datos a almacenar.  
  
 [in] `dwcArray`  
 Referencia a una variable de matriz de doble palabra de 32 bits que contiene los datos a almacenar.  
  
 [in] `wcArray`  
 Referencia a una variable de matriz de palabras de 16 bits que contiene los datos a almacenar.  
  
 [in] `rect`  
 Hacer referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) variable que contiene los datos a almacenar.  
  
 [in] `lpPoint`  
 Referencia a un puntero a un `POINT` variable que contiene los datos a almacenar.  
  
 [in] `pData`  
 Puntero a un búfer que contiene los datos a almacenar.  
  
 [in] `nBytes`  
 Especifica el tamaño, en bytes, de los datos a la que el `pData` puntos de parámetro.  
  
 [in] `list`  
 Hacer referencia a un [CObList](../../mfc/reference/coblist-class.md) variable que contiene los datos a almacenar.  
  
 [in] `obj`  
 Hacer referencia a un [CObject](../../mfc/reference/cobject-class.md) variable que contiene los datos a almacenar.  
  
 [in] `pObj`  
 Puntero a un puntero a un `CObject` variable que contiene los datos a almacenar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para escribir en el registro, debe configurar `bReadOnly` en un valor distinto de cero cuando se crea un [CSettingsStore](../../mfc/reference/csettingsstore-class.md) objeto. Para obtener más información, consulte [CSettingsStore::CSettingsStore](#csettingsstore).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)

