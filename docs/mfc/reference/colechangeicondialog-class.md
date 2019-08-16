---
title: Clase COleChangeIconDialog
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504777"
---
# <a name="colechangeicondialog-class"></a>Clase COleChangeIconDialog

Se utiliza en el cuadro de diálogo Cambiar icono de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construye un objeto `COleChangeIconDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Realiza el cambio especificado en el cuadro de diálogo.|
|[COleChangeIconDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Cambiar icono de OLE 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado al formulario de iconos de este elemento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COleChangeIconDialog` cuando desee llamar a este cuadro de diálogo. Una vez `COleChangeIconDialog` construido un objeto, puede usar la estructura [m_ci](#m_ci) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_ci` estructura es de tipo OLEUICHANGEICON. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea la función miembro [DoModal](#domodal) .

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog

Esta función solo crea un `COleChangeIconDialog` objeto.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a convertir.

*dwFlags*<br/>
Marca de creación, que contiene cualquier número de los siguientes valores combinados mediante el operador OR bit a bit:

- CIF_SELECTCURRENT especifica que el botón de radio actual se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado.

- CIF_SELECTDEFAULT especifica que el botón de radio predeterminado se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CIF_SELECTFROMFILE especifica que el botón de radio desde archivo se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CIF_SHOWHELP especifica que el botón ayuda se mostrará cuando se llame al cuadro de diálogo.

- CIF_USEICONEXE especifica que el icono debe extraerse del archivo ejecutable especificado en el `szIconExe` campo de [m_ci](#m_ci) en lugar de recuperarse del tipo. Esto resulta útil para insertar o vincular archivos que no son de OLE.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon

Llame a esta función para cambiar el icono que representa el elemento a la seleccionada en el cuadro de diálogo después de que [DoModal](#domodal) devuelva IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento cuyo icono está cambiando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cambio se realiza correctamente; de lo contrario, es 0.

##  <a name="domodal"></a>  COleChangeIconDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Cambiar icono de OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_ci](#m_ci) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información que el usuario ha introducido en el cuadro de diálogo.

##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Llame a esta función para obtener un identificador para el metarchivo que contiene el aspecto de los iconos del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo que contiene el aspecto de los iconos del nuevo icono, si el cuadro de diálogo se descartó al elegir **Aceptar**; en caso contrario, el icono tal como estaba antes de que se mostrara el cuadro de diálogo.

##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci

Estructura de tipo OLEUICHANGEICON que se usa para controlar el comportamiento del cuadro de diálogo Cambiar icono.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
