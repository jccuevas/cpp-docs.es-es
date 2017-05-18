---
title: Clase CSettingsStoreSP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP class
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 18
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 00131a3c03fdb2c1c1de247a8e1bdcfd9beaf852
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="csettingsstoresp-class"></a>Clase CSettingsStoreSP
El `CSettingsStoreSP` clase es una clase auxiliar que puede utilizar para crear instancias de la [CSettingsStore clase](../../mfc/reference/csettingsstore-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Construye un objeto `CSettingsStoreSP`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|Crea una instancia de una clase que se deriva de `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Establece la clase en tiempo de ejecución. El `Create` método usa la clase en tiempo de ejecución para determinar qué clase de objetos que se va a crear.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`m_dwUserData`|Datos de usuario personalizado que se almacenarán en la `CSettingsStoreSP` objeto. Proporcione estos datos en el constructor de la `CSettingsStoreSP` objeto.|  
|`m_pRegistry`|El `CSettingsStore`-derivado de objeto que el `Create` método crea.|  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el `CSettingsStoreSP` clase para redirigir todas las operaciones de registro MFC a otras ubicaciones, como un archivo XML o una base de datos. Para ello, siga estos pasos:  
  
1.  Cree una clase (como `CMyStore`) y lo derivará de `CSettingsStore`.  
  
2.  Utilice [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) macros con personalizado `CSettingsStore` clase para habilitar la creación dinámica.  
  
3.  Reemplace las funciones virtuales e implemente el `Read` y `Write` las funciones de la clase personalizada. Implementar cualquier otra funcionalidad para leer y escribir datos en la ubicación deseada.  
  
4.  En la aplicación, llame a `CSettingsStoreSP::SetRuntimeClass` y pase un puntero a la [estructura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obtenidos de la clase.  
  
 Cada vez que el marco obtendría acceso normalmente el registro, lo ahora dinámicamente crear una instancia de la clase personalizada y utilizarla para leer o escribir datos.  
  
 `CSettingsStoreSP::SetRuntimeClass`utiliza una variable estática global. Por lo tanto, sólo un almacén personalizado está disponible en un momento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsettingsstore.h  
  
##  <a name="create"></a>CSettingsStoreSP::Create  
 Crea una nueva instancia de un objeto que se deriva de la [CSettingsStore clase](../../mfc/reference/csettingsstore-class.md).  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAdmin`  
 Un parámetro booleano que determina si un `CSettingsStore` objeto se crea en modo de administrador.  
  
 [in] `bReadOnly`  
 Un parámetro booleano que determina si un `CSettingsStore` se crea el objeto para el acceso de sólo lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la recién creado `CSettingsStore` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el método [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) para determinar qué tipo de objeto `CSettingsStoreSP::Create` , se creará. De forma predeterminada, este método crea un `CSettingsStore` objeto.  
  
 Si crea un `CSettingsStore` objeto en modo de administrador, la ubicación predeterminada para todos los accesos del registro HKEY_LOCAL_MACHINE. De lo contrario, la ubicación predeterminada para todo el acceso del registro es HKEY_CURRENT_USER.  
  
 Si `bAdmin` es `TRUE`, la aplicación debe tener derechos de administración. De lo contrario, producirá un error cuando intenta tener acceso al registro.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CSettingsStoreSP` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp Nº&33;](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP  
 Construye un [CSettingsStoreSP clase](../../mfc/reference/csettingsstoresp-class.md) objeto.  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwUserData`  
 Datos definidos por el usuario que la `CSettingsStoreSP` objeto almacenes.  
  
### <a name="remarks"></a>Comentarios  
 El `CSettingsStoreSP` objeto almacena los datos de `dwUserData` en la variable de miembro protegido `m_dwUserData`.  
  
##  <a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass  
 Establece la clase en tiempo de ejecución. El método [CSettingsStoreSP::Create](#create) usa la clase en tiempo de ejecución para determinar qué tipo de objeto que se va a crear.  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRTI`  
 Un puntero a la información de clase en tiempo de ejecución para una clase derivada de la [CSettingsStore clase](../../mfc/reference/csettingsstore-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` si la clase identificada por `pRTI` no se derive de `CSettingsStore`.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar el [CSettingsStoreSP clase](../../mfc/reference/csettingsstoresp-class.md) derivar clases de `CSettingsStore`. Utilice el método `SetRuntimeClass` si desea crear objetos de una clase personalizada que se deriva de `CSettingsStore`.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CSettingsStore](../../mfc/reference/csettingsstore-class.md)

