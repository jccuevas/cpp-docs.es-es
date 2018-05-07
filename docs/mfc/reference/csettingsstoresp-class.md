---
title: Clase CSettingsStoreSP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1852f4e280fa49a2436c421d4669e9d735d66c3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="csettingsstoresp-class"></a>Clase CSettingsStoreSP
El `CSettingsStoreSP` clase es una clase auxiliar que puede usar para crear instancias de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Construye un objeto `CSettingsStoreSP`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|Crea una instancia de una clase que se deriva de `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Establece la clase en tiempo de ejecución. El `Create` método usa la clase en tiempo de ejecución para determinar qué clase de objetos que se va a crear.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|`m_dwUserData`|Datos de usuario personalizado que se almacenarán en la `CSettingsStoreSP` objeto. Proporcione estos datos en el constructor de la `CSettingsStoreSP` objeto.|  
|`m_pRegistry`|El `CSettingsStore`-derivado del objeto que el `Create` método crea.|  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el `CSettingsStoreSP` clase para redirigir todas las operaciones de registro MFC a otras ubicaciones, como un archivo XML o una base de datos. Para ello, siga estos pasos:  
  
1.  Cree una clase (como `CMyStore`) y lo derivará de `CSettingsStore`.  
  
2.  Use [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) macros con personalizado `CSettingsStore` clase para habilitar la creación dinámica.  
  
3.  Reemplace las funciones virtuales e implemente el `Read` y `Write` las funciones de la clase personalizada. Implementar ninguna otra funcionalidad para leer y escribir datos en la ubicación deseada.  
  
4.  En la aplicación, llame a `CSettingsStoreSP::SetRuntimeClass` y pase un puntero a la [CRuntimeClass estructura](../../mfc/reference/cruntimeclass-structure.md) obtenidas de la clase.  
  
 Cada vez que el marco de trabajo normalmente tendrían acceso del registro, se ahora dinámicamente crear una instancia de la clase personalizada y utilizarla para leer o escribir datos.  
  
 `CSettingsStoreSP::SetRuntimeClass` utiliza una variable estática global. Por lo tanto, solo un almacén personalizado está disponible en un momento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxsettingsstore.h  
  
##  <a name="create"></a>  CSettingsStoreSP::Create  
 Crea una nueva instancia de un objeto que se deriva de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAdmin`  
 Un parámetro booleano que determina si un `CSettingsStore` objeto se crea en modo de administrador.  
  
 [in] `bReadOnly`  
 Un parámetro booleano que determina si un `CSettingsStore` se crea el objeto para el acceso de solo lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la recién creado `CSettingsStore` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar el método [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) para determinar qué tipo de objeto `CSettingsStoreSP::Create` va a crear. De forma predeterminada, este método crea un `CSettingsStore` objeto.  
  
 Si crea un `CSettingsStore` de objeto en el modo de administrador, la ubicación predeterminada para todo el acceso del registro es HKEY_LOCAL_MACHINE. En caso contrario, la ubicación predeterminada para todo el acceso del registro es HKEY_CURRENT_USER.  
  
 Si `bAdmin` es `TRUE`, la aplicación debe tener derechos de administración. En caso contrario, se producirá cuando intenta tener acceso al registro.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CSettingsStoreSP` clase.  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP  
 Construye un [CSettingsStoreSP clase](../../mfc/reference/csettingsstoresp-class.md) objeto.  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwUserData`  
 Datos definidos por el usuario que la `CSettingsStoreSP` almacenes de objetos.  
  
### <a name="remarks"></a>Comentarios  
 El `CSettingsStoreSP` objeto almacena los datos de `dwUserData` en la variable de miembro protegido `m_dwUserData`.  
  
##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass  
 Establece la clase en tiempo de ejecución. El método [CSettingsStoreSP::Create](#create) usa la clase en tiempo de ejecución para determinar qué tipo de objeto que se va a crear.  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRTI`  
 Un puntero a la información de clase en tiempo de ejecución para una clase derivada de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si se realiza correctamente; `FALSE` si la clase identificada por `pRTI` no se deriva de `CSettingsStore`.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar el [CSettingsStoreSP clase](../../mfc/reference/csettingsstoresp-class.md) para derivar clases desde `CSettingsStore`. Utilice el método `SetRuntimeClass` si desea crear objetos de una clase personalizada que se deriva de `CSettingsStore`.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSettingsStore (clase)](../../mfc/reference/csettingsstore-class.md)
