---
title: CWinFormsDialog (clase)
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367425"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog (clase)

Un contenedor para una clase de cuadro de diálogo MFC que hospeda un control de usuario de formularios Windows Forms.

## <a name="syntax"></a>Sintaxis

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parámetros

*TManagedControl*<br/>
El control de usuario de .NET Framework que se mostrará en la aplicación MFC.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Construye un objeto `CWinFormsDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Recupera una referencia al control de usuario de formularios Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Recupera un identificador de ventana para el control de usuario de formularios Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicializa el cuadro de diálogo MFC mediante la creación y el hospedaje de un control de usuario de formularios Windows Forms en él.|

### <a name="public-operators"></a>Operadores públicos

|Nombre||
|----------|-|
|[CWinFormsDialog::operador -&gt;](#operator_-_gt)|Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.|
|[CWinFormsDialog::operador TManagedControl](#operator-tmanagedcontrol-hat)|Convierte un tipo como referencia a un control de usuario de formularios Windows Forms.|

## <a name="remarks"></a>Observaciones

`CWinFormsDialog`es un contenedor para una clase de cuadro de diálogo MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) que hospeda un control de usuario de formularios Windows Forms. Esto permite mostrar controles de .NET Framework en un cuadro de diálogo MFC modal o no modal.

Para obtener más información sobre el uso de formularios Windows Forms, vea Usar un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) y Hospedar un control de usuario de formulario Windows Como un cuadro de diálogo [MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog

Construye un objeto `CWinFormsDialog`.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
Contiene el identificador de un recurso de plantilla de cuadro de diálogo. Utilice el editor de cuadros de diálogo para crear la plantilla de cuadro de diálogo y almacenarla en el archivo de script de recursos de la aplicación. Para obtener más información sobre las plantillas de cuadro de diálogo, vea [CDialog (Clase)](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::GetControl

Recupera una referencia al control de usuario de formularios Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al control de formularios Windows Forms en el cuadro de diálogo MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle

Recupera un identificador de ventana para el control de usuario de formularios Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador de ventana al control de usuario de formularios Windows Forms.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog

Inicializa el cuadro de diálogo MFC mediante la creación y el hospedaje de un control de usuario de formularios Windows Forms en él.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Valor booleano que especifica si la aplicación ha establecido el foco de entrada en uno de los controles del cuadro de diálogo. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada en el primer control del cuadro de diálogo. Este método solo puede devolver 0 si la aplicación ha establecido explícitamente el foco de entrada en uno de los controles del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Cuando se crea el cuadro de diálogo MFC (mediante el método [Create](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)o [DoModal](../../mfc/reference/cdialog-class.md#domodal) heredado de [CDialog](../../mfc/reference/cdialog-class.md)), se envía un mensaje de WM_INITDIALOG y se llama a este método. Crea una instancia de un control de formularios Windows Forms en el cuadro de diálogo y ajusta el tamaño del cuadro de diálogo para adaptarse al tamaño del control de usuario. A continuación, hospeda el nuevo control en el cuadro de diálogo MFC.

Invalide esta función miembro si necesita realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. Para obtener más información sobre el uso de este método, vea [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::operador -&gt;

Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Observaciones

Este operador proporciona una sintaxis conveniente que reemplaza `GetControl` en expresiones.

Para obtener información sobre el uso de formularios Windows Forms, vea Uso de un control de usuario de [formularios Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinFormsDialog::operador TManagedControl

Convierte un tipo como referencia a un control de usuario de formularios Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Observaciones

Este operador convierte un tipo como una referencia a un control de formularios Windows Forms. Se utiliza para `CWinFormsDialog<TManagedControl>` pasar un cuadro de diálogo a funciones que aceptan un puntero a un objeto de control de usuario de formularios Windows Forms.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
