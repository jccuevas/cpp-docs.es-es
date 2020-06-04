---
title: CWinFormsControl (clase)
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377176"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl (clase)

Proporciona la funcionalidad básica para hospedar un control de formularios Windows Forms.

## <a name="syntax"></a>Sintaxis

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parámetros

*TManagedControl*<br/>
Un control de formularios Windows Forms de .NET Framework que se mostrará en la aplicación MFC.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construye un objeto contenedor de controles de formularios Windows Forms MFC.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Crea un control de formularios Windows Forms en un contenedor MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Recupera un puntero al control de formularios Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Recupera un identificador para el control de formularios Windows Forms.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsControl::operador -&gt;](#operator_-_gt)|Reemplaza [CWinFormsControl::GetControl](#getcontrol) en expresiones.|
|[CWinFormsControl::operador TManagedControl](#operator_tmanagedcontrol)|Convierte un tipo como un puntero a un control de formularios Windows Forms.|

## <a name="remarks"></a>Observaciones

La `CWinFormsControl` clase proporciona la funcionalidad básica para hospedar un control de formularios Windows Forms.

Para obtener más información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

El código MFC no debe almacenar `m_hWnd`en caché los identificadores Window (normalmente almacenados en ). Algunas propiedades de control de formularios `Window` Windows Forms requieren que `DestroyWindow` `CreateWindow`el Win32 subyacente se destruya y vuelva a crear mediante y . La implementación de `Destroy` formularios `Create` Windows Forms de `m_hWnd` MFC controla los eventos y de los controles para actualizar el miembro.

> [!NOTE]
> La integración de formularios Windows Forms de MFC solo funciona en proyectos que se vinculan dinámicamente con MFC (en el que se define AFXDLL).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Crea un control de formularios Windows Forms en un contenedor MFC.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Parámetros

*pType*<br/>
El tipo de datos del control que se va a crear. Debe ser un tipo de datos [Type.](/dotnet/api/system.type)

*dwStyle*<br/>
El estilo de ventana que se aplicará al control. Especifique una combinación de [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana . Actualmente, solo se admiten los siguientes estilos: WS_TABSTOP, WS_VISIBLE, WS_DISABLED y WS_GROUP.

*Rect*<br/>
Estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que define las coordenadas de las esquinas superior izquierda e inferior derecha del control (solo primera sobrecarga).

*nPlaceHolderID*<br/>
Identificador del control de soporte de posición estático colocado en el Editor de recursos. El control de formularios Windows Forms recién creado reemplaza el control estático, suponiendo su posición, orden z y estilos (segunda sobrecarga solamente).

*pParentWnd*<br/>
Puntero en la ventana primaria.

*nID*<br/>
El número de ID de recurso que se asignará al control recién creado.

*pControl*<br/>
Una instancia de un control de formularios Windows Forms que se asociará con el [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) objeto (cuarta sobrecarga solamente).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve un valor distinto de cero. Si no se realiza correctamente, devuelve cero.

### <a name="remarks"></a>Observaciones

Este método crea una instancia de un control de formularios Windows Forms de .NET Framework en un contenedor MFC.

La primera sobrecarga del método acepta un tipo de datos de .NET Framework *pType* para que MFC pueda crear instancias de un nuevo objeto de este tipo. *pType* debe ser un tipo de datos [Type.](/dotnet/api/system.type)

La segunda sobrecarga del método crea un `TManagedControl` control de `CWinFormsControl` formularios Windows Forms basado en el parámetro template de la clase. El tamaño y la posición del `RECT` control se basa en la estructura pasada al método. Solo *dwStyle* importa para los estilos.

La tercera sobrecarga del método crea un control de formularios Windows Forms que reemplaza un control estático, destruyéndolo y suponiendo su posición, orden z y estilos. El control estático solo sirve como marcador de posición para el control de formularios Windows Forms. Al crear el control, esta sobrecarga combina los estilos de *dwStyle* con los estilos de recursos del control estático.

La cuarta sobrecarga del método permite pasar un control *pControl* de formularios Windows Forms ya creado que MFC ajustará. Debe ser del mismo tipo `TManagedControl` que el `CWinFormsControl` parámetro de plantilla de la clase.

Consulte Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) para obtener ejemplos sobre el uso de controles de formulario Windows Forms.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Construye un objeto contenedor de controles de formularios Windows Forms MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Observaciones

Se crea una instancia del control de formularios Windows Forms cuando se llama a [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinFormsControl::GetControl

Recupera un puntero al control de formularios Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al control de formularios Windows Forms.

### <a name="example"></a>Ejemplo

  Vea [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Recupera un identificador para el control de formularios Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el control de formularios Windows Forms.

### <a name="remarks"></a>Observaciones

`GetControlHandle`es un método auxiliar que devuelve el identificador de ventana almacenado en las propiedades del control de .NET Framework. El valor del identificador de ventana se copia en [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) durante la llamada a [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::operador -&gt;

Reemplaza [CWinFormsControl::GetControl](#getcontrol) en expresiones.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Observaciones

Este operador proporciona una sintaxis conveniente que reemplaza `GetControl` en expresiones.

Para obtener más información sobre formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::operador TManagedControl

Convierte un tipo como un puntero a un control de formularios Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Observaciones

Este operador `CWinFormsControl<TManagedControl>` pasa a funciones que aceptan un puntero a un control de formularios Windows Forms.

## <a name="see-also"></a>Consulte también

[CWinFormsDialog (clase)](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)
