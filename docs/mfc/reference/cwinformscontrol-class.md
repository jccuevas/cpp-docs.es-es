---
title: CWinFormsControl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d687c2ffc0659e1a0571f55528dd35044d154dad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053830"
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
Un control de Windows Forms de .NET Framework que se mostrará en la aplicación MFC.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construye un objeto de contenedor de control de formularios Windows Forms de MFC.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)|Crea un control de Windows Forms en un contenedor de MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Recupera un puntero al control de Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Recupera un identificador para el control Windows Forms.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Reemplaza [CWinFormsControl::GetControl](#getcontrol) en expresiones.|
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Convierte un tipo de puntero a un control de Windows Forms.|

## <a name="remarks"></a>Comentarios

La `CWinFormsControl` clase proporciona la funcionalidad básica para hospedar un control de Windows Forms.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

El código MFC no debe almacenar en caché identificadores de ventana (normalmente se almacena en `m_hWnd`). Algunas propiedades de control de Windows Forms requieren que Win32 subyacente `Window` destruirse y volver a crearlos con `DestroyWindow` y `CreateWindow`. Los identificadores de la implementación de formularios Windows Forms de MFC la `Destroy` y `Create` eventos de los controles para actualizar el `m_hWnd` miembro.

> [!NOTE]
>  Integración de formularios Windows Forms de MFC sólo funciona en los proyectos que se vinculan dinámicamente con MFC (en el que se ha definido AFXDLL).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl:: CreateManagedControl

Crea un control de Windows Forms en un contenedor de MFC.

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

*PEscriba*<br/>
El tipo de datos del control que se va a crear. Debe ser un [tipo](https://msdn.microsoft.com/library/system.type) tipo de datos.

*dwStyle*<br/>
Estilo de ventana que se va a aplicar al control. Especificar una combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles). Actualmente, se admiten solo los siguientes estilos: WS_TABSTOP, WS_VISIBLE, WS_DISABLED y WS_GROUP.

*Rect*<br/>
Un [estructura RECT](../../mfc/reference/rect-structure1.md) que define las coordenadas de las esquinas superior izquierda e inferior derecha del control (primera sobrecarga solo).

*nPlaceHolderID*<br/>
El identificador del control de marcador de posición estático se coloca en el Editor de recursos. El control de formularios de Windows recién creado reemplaza al control estático, suponiendo que su posición, el orden z y los estilos (segunda sobrecarga solo).

*pParentWnd*<br/>
Un puntero a la ventana primaria.

*nID*<br/>
El número de Id. de recurso que se asignará al control recién creado.

*pControl*<br/>
Una instancia de un control de Windows Forms se asocie a la [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (solo la sobrecarga de la cuarta) de objeto.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve un valor distinto de cero. Si no lo consigue, devuelve cero.

### <a name="remarks"></a>Comentarios

Este método crea una instancia de un control de Windows Forms de .NET Framework en un contenedor de MFC.

La primera sobrecarga del método acepta un tipo de datos de .NET Framework *PEscriba* para que MFC puede crear una instancia de un nuevo objeto de este tipo. *PEscriba* debe ser un [tipo](https://msdn.microsoft.com/library/system.type) tipo de datos.

La segunda sobrecarga del método crea un control de Windows Forms según el `TManagedControl` parámetro de plantilla de la `CWinFormsControl` clase. El tamaño y posición del control se basa en el `RECT` estructura se pasa al método. Solo *dwStyle* es importante para los estilos.

La tercera sobrecarga del método crea un control de Windows Forms que reemplaza un control estático, se destruye y suponiendo que su posición, orden z y estilos. El control estático sólo actúa como un marcador de posición para el control Windows Forms. Al crear el control, esta sobrecarga combina los estilos de *dwStyle* con estilos de recursos del control estático.

El cuarta sobrecarga del método permite pasar en un control de Windows Forms ya tiene instanciado *pControl* que MFC se ajustará. Debe ser del mismo tipo que el `TManagedControl` parámetro de plantilla de la `CWinFormsControl` clase.

Consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) para obtener ejemplos sobre el uso de formulario de Windows controla.

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

Construye un objeto de contenedor de control de formularios Windows Forms de MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Comentarios

El control Windows Forms se crea una instancia cuando se llama a [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

Recupera un puntero al control de Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al control de Windows Forms.

### <a name="example"></a>Ejemplo

  Consulte [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

Recupera un identificador para el control Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el control Windows Forms.

### <a name="remarks"></a>Comentarios

`GetControlHandle` es un método auxiliar que devuelve el identificador de ventana que se almacenan en las propiedades del control de .NET Framework. El valor del identificador de ventana se copia en [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) durante la llamada a [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;

Reemplaza [CWinFormsControl::GetControl](#getcontrol) en expresiones.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Comentarios

Este operador proporciona una sintaxis adecuada que reemplaza `GetControl` en expresiones.

Para obtener más información sobre Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^

Convierte un tipo de puntero a un control de Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Comentarios

Este operador pasa `CWinFormsControl<TManagedControl>` a las funciones que aceptan un puntero a un control Windows Forms.

## <a name="see-also"></a>Vea también

[CWinFormsDialog (clase)](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)
