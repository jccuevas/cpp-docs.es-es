---
title: Clase CMFCEditBrowseCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: 31fadc0a960ddfcf216951e1af481983b122ea0f
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821304"
---
# <a name="cmfceditbrowsectrl-class"></a>Clase CMFCEditBrowseCtrl

La `CMFCEditBrowseCtrl` clase admite el control de búsqueda de edición, que es un cuadro de texto editable que, opcionalmente, contiene un botón examinar. Cuando el usuario hace clic en el botón Examinar, el control realiza una acción personalizada o muestra un cuadro de diálogo estándar que contiene un explorador de archivos o un explorador de carpetas.

## <a name="syntax"></a>Sintaxis

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Constructor predeterminado.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Habilita o deshabilita (oculta) el botón examinar.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Habilita el botón examinar y coloca el control Editar examinar en el modo de *exploración de archivos* .|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Habilita el botón examinar y coloca el control Editar examinar en el modo de *exploración de carpetas* .|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Devuelve el modo de exploración actual.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Lo llama el marco de trabajo después de actualizar el control de exploración de edición con el resultado de una acción de exploración.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Lo llama el marco de trabajo después de que el usuario haga clic en el botón examinar.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Vuelve a dibujar el control de exploración de edición actual.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Lo llama el marco de trabajo para dibujar el botón examinar.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Lo llama el marco de trabajo cuando se escribió un nombre de archivo no válido en el control de edición.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) . Para ver la sintaxis y obtener más información, vea [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Establece una imagen personalizada para el botón examinar.|

## <a name="remarks"></a>Comentarios

Use un control de búsqueda de edición para seleccionar un nombre de archivo o carpeta. Opcionalmente, utilice el control para realizar una acción personalizada como para mostrar un cuadro de diálogo. Puede mostrar o no mostrar el botón examinar y puede aplicar una etiqueta o imagen personalizada en el botón.

El *modo de exploración* del control de búsqueda de edición determina si muestra un botón examinar y la acción que se produce cuando se hace clic en el botón. Para obtener más información, vea el método [GetMode](#getmode) .

La `CMFCEditBrowseCtrl` clase admite los siguientes modos.

- **modo personalizado**

   Cuando el usuario hace clic en el botón examinar, se realiza una acción personalizada. Por ejemplo, puede mostrar un cuadro de diálogo específico de la aplicación.

- **modo de archivo**

   Cuando el usuario hace clic en el botón examinar, se muestra un cuadro de diálogo de selección de archivos estándar.

- **modo de carpeta**

   Cuando el usuario hace clic en el botón examinar, se muestra un cuadro de diálogo de selección de carpeta estándar.

## <a name="how-to-specify-an-edit-browse-control"></a>Uso Especificar un control de búsqueda de edición

Realice los pasos siguientes para incorporar un control de búsqueda de edición en la aplicación:

1. Si desea implementar un modo de exploración personalizado, derive su propia clase de la `CMFCEditBrowseCtrl` clase y, a continuación, invalide el método [CMFCEditBrowseCtrl:: nonbrowse](#onbrowse) . En el método invalidado, ejecute una acción de exploración personalizada y actualice el control de búsqueda de edición con el resultado.

1. Inserte el `CMFCEditBrowseCtrl` objeto o el objeto de control de búsqueda de edición derivado en el objeto de ventana principal.

1. Si usa el **Asistente para clases** para crear un cuadro de diálogo, agregue un control de `CEdit`edición () al formulario del cuadro de diálogo. Además, agregue una variable para tener acceso al control en el archivo de encabezado. En el archivo de encabezado, cambie el tipo de la variable `CEdit` de `CMFCEditBrowseCtrl`a. El control Editar examen se creará automáticamente. Si no usa el **Asistente para clases**, agregue una `CMFCEditBrowseCtrl` variable al archivo de encabezado y, a continuación, `Create` llame a su método.

1. Si agrega un control Editar examinar a un cuadro de diálogo, use la herramienta **ClassWizard** para configurar el intercambio de datos.

1. Llame al método [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)o [EnableBrowseButton](#enablebrowsebutton) para establecer el modo de exploración y mostrar el botón examinar. Llame al método [GetMode](#getmode) para obtener el modo de exploración actual.

1. Para proporcionar una imagen personalizada para el botón examinar, llame al método [SetBrowseButtonImage](#setbrowsebuttonimage) o invalide el método [OnDrawBrowseButton](#ondrawbrowsebutton) .

1. Para quitar el botón examinar del control de búsqueda de edición, llame al método [EnableBrowseButton](#enablebrowsebutton) con el parámetro *BENABLE* establecido en false.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar dos métodos en `CMFCEditBrowseCtrl` la clase `EnableFolderBrowseButton` : `EnableFileBrowseButton`y. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxeditbrowsectrl. h

##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton

Muestra o no muestra el botón examinar en el control Editar examinar actual.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
TRUE para mostrar el botón examinar; FALSE para mostrar el botón examinar. El valor predeterminado es TRUE.

*szLabel*<br/>
La etiqueta que se muestra en el botón examinar. El valor predeterminado es " **...** ".

### <a name="remarks"></a>Comentarios

Si el parámetro *bEnable* es true, implemente una acción personalizada que se realizará cuando se haga clic en el botón examinar. Para implementar una acción personalizada, derive una clase de la `CMFCEditBrowseCtrl` clase y, a continuación, invalide su método My [Browse](#onbrowse) .

Si el parámetro *bEnable* es true, el modo de exploración del control es `BrowseMode_Default`; de lo contrario, el modo `BrowseMode_None`de exploración es. Para obtener más información sobre los modos de exploración, vea el método [GetMode](#getmode) .

##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton

Muestra el botón examinar en el control Editar examinar actual y coloca el control en el modo de *exploración de archivos* .

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parámetros

*lpszDefExt*<br/>
Especifica la extensión de nombre de archivo predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es NULL.

*lpszFilter*<br/>
Especifica la cadena de filtro predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es NULL.

*dwFlags*<br/>
Marcas de cuadro de diálogo. El valor predeterminado es una combinación bit a bit (OR) de OFN_HIDEREADONLY y OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Comentarios

Cuando el control de cuadro de búsqueda modificable está en modo de búsqueda de archivo y el usuario hace clic en el botón Examinar, el control muestra el cuadro de diálogo de selección de archivos estándar.

Para obtener una lista completa de las marcas disponibles, consulte la [estructura OPENFILENAME](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton

Muestra el botón examinar en el control Editar examinar actual y coloca el control en el modo de *exploración de carpetas* .

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Comentarios

Cuando el control Editar examen está en el modo de exploración de carpetas y el usuario hace clic en el botón examinar, el control muestra el cuadro de diálogo Selección de carpeta estándar.

##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode

Recupera el modo de exploración del control de exploración de edición actual.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Valor devuelto

Uno de los valores de enumeración que especifica el modo actual del control de búsqueda de edición. El modo de exploración determina si el marco de trabajo muestra el botón examinar y la acción que se produce cuando un usuario hace clic en ese botón.

La tabla siguiente muestra los valores devueltos posibles.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|`BrowseMode_Default`|**modo personalizado**. Se realiza una acción definida por el programador.|
|`BrowseMode_File`|**modo de archivo**. Se muestra el cuadro de diálogo de explorador de archivos estándar.|
|`BrowseMode_Folder`|**modo de carpeta**. Se muestra el cuadro de diálogo de explorador de carpetas estándar.|
|`BrowseMode_None`|No se muestra el botón examinar.|

### <a name="remarks"></a>Comentarios

De forma predeterminada, `CMFCEditBrowseCtrl` un objeto se inicializa en `BrowseMode_None` el modo. Modifique el modo de exploración con los métodos [CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)y [CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton) .

##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate

Lo llama el marco de trabajo después de actualizar el control de exploración de edición con el resultado de una acción de exploración.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar una acción personalizada.

##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse

Lo llama el marco de trabajo después de que el usuario haga clic en el botón examinar del control de búsqueda de edición.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Comentarios

Use este método para ejecutar código personalizado cuando el usuario haga clic en el botón examinar del control de búsqueda de edición. Derive su propia clase de la `CMFCEditBrowseCtrl` clase e invalide su `OnBrowse` método. En ese método, implemente una acción de exploración personalizada y, opcionalmente, actualice el cuadro de texto del control de búsqueda de edición. En la aplicación, use el método [EnableBrowseButton](#enablebrowsebutton) para colocar el control Editar examinar en el modo de *exploración personalizado* .

##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout

Vuelve a dibujar el control de exploración de edición actual.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando cambia el modo de exploración del control de búsqueda de edición. Para obtener más información, vea [CMFCEditBrowseCtrl:: GetMode](#getmode).

##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton

Lo llama el marco de trabajo para dibujar el botón examinar en el control Editar examen.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo.

*Rect*<br/>
Rectángulo delimitador del botón examinar.

*bIsButtonPressed*<br/>
TRUE si se presiona el botón; en caso contrario, FALSE.

*bIsButtonHot*<br/>
TRUE si el botón está resaltado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Invalide esta función en una clase derivada para personalizar la apariencia del botón examinar.

##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage

Establece una imagen personalizada en el botón examinar del control de búsqueda de edición.

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
Identificador de un icono.

*hBitmap*<br/>
Identificador de un mapa de bits.

*uiBmpResId*<br/>
El identificador de recurso de un mapa de bits.

*bAutoDestroy*<br/>
TRUE para eliminar el icono o mapa de bits especificado al salir de este método; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Use este método para aplicar una imagen personalizada al botón examinar. De forma predeterminada, el marco de trabajo obtiene una imagen estándar cuando el control de exploración de edición está en modo de exploración de *archivos* o de *búsqueda de carpetas* .

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

Lo llama el marco de trabajo cuando se escribió un nombre de archivo no válido en el control de edición.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parámetros

*strFileName*<br/>
Especifica el nombre de archivo no válido.

### <a name="return-value"></a>Valor devuelto

Debe devolver FALSE si este nombre de archivo no se puede pasar más al cuadro de diálogo de archivo. En este caso, el foco se vuelve a establecer en el control de edición y el usuario debe continuar con la edición. La implementación predeterminada muestra un cuadro de mensaje que indica al usuario el nombre de archivo no válido y devuelve FALSE. Puede invalidar este método, corregir el nombre de archivo y devolver TRUE para su posterior procesamiento.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
