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
ms.openlocfilehash: 1542f852a8fe3f05d81ae59efb8a522caae671fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323416"
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

|Name|Descripción|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Construye un objeto `CWinFormsDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Recupera una referencia al control de usuario de Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Recupera un identificador de ventana para el control de usuario de Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicializa el cuadro de diálogo MFC mediante la creación y hospedar un control de usuario de Windows Forms en él.|

### <a name="public-operators"></a>Operadores públicos

|Name||
|----------|-|
|[CWinFormsDialog::operator -&gt;](#operator_-_gt)|Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.|
|[CWinFormsDialog::operator TManagedControl ^](#operator-tmanagedcontrol-hat)|Convierte un tipo como una referencia a un control de usuario de Windows Forms.|

## <a name="remarks"></a>Comentarios

`CWinFormsDialog` es un contenedor para una clase de cuadro de diálogo MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) que hospeda un control de usuario de Windows Forms. Esto permite la visualización de los controles de .NET Framework en un cuadro de diálogo MFC modal o no modal.

Para obtener más información sobre el uso de Windows Forms, consulte [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) y [hospedar un Control de usuario de Windows Forms como un cuadro de diálogo de MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwinforms.h

##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog

Construye un objeto `CWinFormsDialog`.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
Contiene el identificador de un recurso de plantilla de cuadro de diálogo. Usar el editor de cuadro de diálogo para crear la plantilla de cuadro de diálogo y almacenarlo en el archivo de script de recursos de la aplicación. Para obtener más información sobre las plantillas de cuadro de diálogo, vea [CDialog (clase)](../../mfc/reference/cdialog-class.md).

##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl

Recupera una referencia al control de usuario de Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al control de Windows Forms en el cuadro de diálogo MFC.

##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle

Recupera un identificador de ventana para el control de usuario de Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador de ventana para el control de usuario de Windows Forms.

##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog

Inicializa el cuadro de diálogo MFC mediante la creación y hospedar un control de usuario de Windows Forms en él.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Un valor booleano que especifica si la aplicación ha establecido el foco de entrada en uno de los controles en el cuadro de diálogo. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada en el primer control en el cuadro de diálogo. Este método puede devolver 0 solo si la aplicación establece explícitamente el foco de entrada para uno de los controles en el cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Cuando se crea el cuadro de diálogo MFC (mediante el [crear](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), o [DoModal](../../mfc/reference/cdialog-class.md#domodal) método hereda [CDialog](../../mfc/reference/cdialog-class.md)), un WM_ Se envía el mensaje INITDIALOG y se llama a este método. Crea una instancia de un control de Windows Forms en el cuadro de diálogo y ajusta el tamaño del cuadro de diálogo para acomodar el tamaño del control de usuario. A continuación, hospeda el nuevo control en el cuadro de diálogo MFC.

Reemplace esta función miembro si tiene que realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. Para obtener más información sobre el uso de este método, consulte [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator -&gt;

Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Comentarios

Este operador proporciona una sintaxis adecuada que reemplaza `GetControl` en expresiones.

Para obtener información sobre el uso de Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator-tmanagedcontrol-hat"></a>  CWinFormsDialog::operator TManagedControl ^

Convierte un tipo como una referencia a un control de usuario de Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Comentarios

Este operador convierte un tipo como una referencia a un control Windows Forms. Se utiliza para pasar un `CWinFormsDialog<TManagedControl>` cuadro de diálogo para las funciones que aceptan un puntero a un objeto de control de usuario de Windows Forms.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView (clase)](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
