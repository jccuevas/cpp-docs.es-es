---
title: Clase CSettingsStoreSP
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318452"
---
# <a name="csettingsstoresp-class"></a>Clase CSettingsStoreSP

La `CSettingsStoreSP` clase es una clase auxiliar que puede utilizar para crear instancias de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).

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
|[CSettingsStoreSP::Crear](#create)|Crea una instancia de una clase `CSettingsStore`que se deriva de .|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Establece la clase en tiempo de ejecución. El `Create` método utiliza la clase en tiempo de ejecución para determinar qué clase de objetos se creará.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|`m_dwUserData`|Datos de usuario personalizados `CSettingsStoreSP` que se almacenan en el objeto. Estos datos se proporcionan en `CSettingsStoreSP` el constructor del objeto.|
|`m_pRegistry`|El `CSettingsStore`objeto -derived `Create` que crea el método.|

## <a name="remarks"></a>Observaciones

Puede usar `CSettingsStoreSP` la clase para redirigir todas las operaciones del Registro MFC a otras ubicaciones, como un archivo XML o una base de datos. Para ello, siga estos pasos.

1. Cree una clase `CMyStore`(como ) `CSettingsStore`y derivarla de .

1. Utilice [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) `CSettingsStore` macros con la clase personalizada para habilitar la creación dinámica.

1. Invalide las funciones `Read` `Write` virtuales e implemente las funciones y en la clase personalizada. Implemente cualquier otra funcionalidad para leer y escribir datos en la ubicación deseada.

1. En la aplicación, llame `CSettingsStoreSP::SetRuntimeClass` y pase un puntero a la Estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obtenida de la clase.

Siempre que el marco de trabajo normalmente tendría acceso al registro, ahora creará instancias dinámicas de la clase personalizada y la usará para leer o escribir datos.

`CSettingsStoreSP::SetRuntimeClass`utiliza una variable estática global. Por lo tanto, solo hay una tienda personalizada disponible a la vez.

## <a name="requirements"></a>Requisitos

**Encabezado:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP::Crear

Crea una nueva instancia de un objeto que se deriva de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parámetros

*bAdmin*<br/>
[en] Parámetro booleano que determina `CSettingsStore` si se crea un objeto en modo de administrador.

*bReadOnly*<br/>
[en] Parámetro booleano que determina `CSettingsStore` si se crea un objeto para el acceso de solo lectura.

### <a name="return-value"></a>Valor devuelto

Una referencia al `CSettingsStore` objeto recién creado.

### <a name="remarks"></a>Observaciones

Puede utilizar el método [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) para `CSettingsStoreSP::Create` determinar qué tipo de objeto creará. De forma predeterminada, `CSettingsStore` este método crea un objeto.

Si crea `CSettingsStore` un objeto en modo de administrador, la ubicación predeterminada para todo el acceso al Registro es HKEY_LOCAL_MACHINE. De lo contrario, la ubicación predeterminada para todo el acceso al Registro es HKEY_CURRENT_USER.

Si *bAdmin* es TRUE, la aplicación debe tener derechos de administración. De lo contrario, se producirá un error cuando intente acceder al registro.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `Create` muestra `CSettingsStoreSP` cómo utilizar el método de la clase.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP

Construye un [CSettingsStoreSP clase](../../mfc/reference/csettingsstoresp-class.md) objeto.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*dwUserData*<br/>
[en] Datos definidos por `CSettingsStoreSP` el usuario que almacena el objeto.

### <a name="remarks"></a>Observaciones

El `CSettingsStoreSP` objeto almacena los datos de *dwUserData* en la variable `m_dwUserData`miembro protegida .

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass

Establece la clase en tiempo de ejecución. El método [CSettingsStoreSP::Create](#create) utiliza la clase en tiempo de ejecución para determinar qué tipo de objeto se va a crear.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parámetros

*pRTI*<br/>
[en] Puntero a la información de clase en tiempo de ejecución para una clase derivada de la [clase CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente; FALSE si la clase identificada por *pRTI* no se deriva de `CSettingsStore`.

### <a name="remarks"></a>Observaciones

Puede utilizar la [clase CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) `CSettingsStore`para derivar clases de . Utilice el `SetRuntimeClass` método si desea crear objetos de una `CSettingsStore`clase personalizada derivada de .

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)
