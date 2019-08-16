---
title: Clase CWinFormsControl
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
ms.openlocfilehash: 75a6d7ea2b4f3ab229d7e3f4d411711261bb1b82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502190"
---
# <a name="cwinformscontrol-class"></a>Clase CWinFormsControl

Proporciona la funcionalidad básica para hospedar un control de formularios Windows Forms.

## <a name="syntax"></a>Sintaxis

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parámetros

*TManagedControl*<br/>
.NET Framework Windows Forms control que se va a mostrar en la aplicación MFC.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construye un objeto contenedor de controles de Windows Forms MFC.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Crea un control de Windows Forms en un contenedor MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Recupera un puntero al control Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Recupera un identificador del control Windows Forms.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinFormsControl::operator -&gt;](#operator_-_gt)|Reemplaza [CWinFormsControl:: GetControl](#getcontrol) en expresiones.|
|[CWinFormsControl:: Operator TManagedControl ^](#operator_tmanagedcontrol)|Convierte un tipo en un puntero a un control de Windows Forms.|

## <a name="remarks"></a>Comentarios

La `CWinFormsControl` clase proporciona la funcionalidad básica para hospedar un control Windows Forms.

Para obtener más información sobre el uso de Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

El código MFC no debe almacenar en caché los identificadores de `m_hWnd`ventana (normalmente almacenados en). Algunas propiedades de control de Windows Forms requieren que el `Window` Win32 subyacente se destruya y se vuelva `DestroyWindow` a `CreateWindow`crear con y. La implementación de Windows Forms de MFC `Destroy` controla `Create` los eventos y de los controles para `m_hWnd` actualizar el miembro.

> [!NOTE]
>  La integración de Windows Forms MFC solo funciona en proyectos que se vinculan dinámicamente con MFC (en el que se define AFXDLL).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms. h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

Crea un control de Windows Forms en un contenedor MFC.

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
El tipo de datos del control que se va a crear. Debe ser un tipo de datos de [tipo](/dotnet/api/system.type) .

*dwStyle*<br/>
Estilo de ventana que se va a aplicar al control. Especifique una combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles). Actualmente, solo se admiten los siguientes estilos: WS_TABSTOP, WS_VISIBLE, WS_DISABLED y WS_GROUP.

*rect*<br/>
[Estructura Rect](/windows/win32/api/windef/ns-windef-rect) que define las coordenadas de las esquinas superior izquierda e inferior derecha del control (solo la primera sobrecarga).

*nPlaceHolderID*<br/>
Identificador del control de marcador de posición estático colocado en el editor de recursos. El control Windows Forms recién creado reemplaza el control estático, suponiendo su posición, el orden z y los estilos (solo la segunda sobrecarga).

*pParentWnd*<br/>
Puntero a la ventana primaria.

*nID*<br/>
El número de ID. de recurso que se va a asignar al control recién creado.

*pControl*<br/>
Una instancia de un control Windows Forms que se va a asociar al objeto [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (solo la cuarta sobrecarga).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve un valor distinto de cero. Si no se realiza correctamente, devuelve cero.

### <a name="remarks"></a>Comentarios

Este método crea una instancia de un .NET Framework Windows Forms control en un contenedor MFC.

La primera sobrecarga del método acepta un .NET Framework del tipo de datos *pType* para que MFC pueda crear instancias de un nuevo objeto de este tipo. *pType* debe ser un tipo de datos de [tipo](/dotnet/api/system.type) .

La segunda sobrecarga del método crea un control de Windows Forms basado en el `TManagedControl` parámetro de plantilla de `CWinFormsControl` la clase. El tamaño y la posición del control se basan en la `RECT` estructura que se pasa al método. Solo *dwStyle* es importante para los estilos.

La tercera sobrecarga del método crea un control Windows Forms que reemplaza un control estático, lo destruye y asume su posición, el orden z y los estilos. El control estático solo sirve como marcador de posición para el control Windows Forms. Al crear el control, esta sobrecarga combina los estilos de *dwStyle* con los estilos de recursos del control estático.

La cuarta sobrecarga del método permite pasar un *pControl* de control de Windows Forms de instancias que se va a incluir en la instancia de MFC. Debe ser del mismo tipo que el `TManagedControl` parámetro de plantilla de la `CWinFormsControl` clase.

Vea [usar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) para obtener ejemplos sobre el uso de controles de Windows Forms.

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

Construye un objeto contenedor de controles de Windows Forms MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Comentarios

Se crea una instancia del control Windows Forms cuando se llama a [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

Recupera un puntero al control Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al control Windows Forms.

### <a name="example"></a>Ejemplo

  Vea [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

Recupera un identificador del control Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el control Windows Forms.

### <a name="remarks"></a>Comentarios

`GetControlHandle`es un método auxiliar que devuelve el identificador de ventana almacenado en las propiedades del control .NET Framework. El valor del identificador de ventana se copia en [CWnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) durante la llamada a [CWnd:: Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator -&gt;

Reemplaza [CWinFormsControl:: GetControl](#getcontrol) en expresiones.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Comentarios

Este operador proporciona una sintaxis adecuada que reemplaza `GetControl` en expresiones.

Para obtener más información sobre Windows Forms, vea [utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>CWinFormsControl:: Operator TManagedControl ^

Convierte un tipo en un puntero a un control de Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Comentarios

Este operador pasa `CWinFormsControl<TManagedControl>` a las funciones que aceptan un puntero a un control de Windows Forms.

## <a name="see-also"></a>Vea también

[CWinFormsDialog (clase)](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)
