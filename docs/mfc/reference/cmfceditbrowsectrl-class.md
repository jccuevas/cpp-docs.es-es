---
title: CMFCEditBrowseCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0da6941a3076b23eb127cdcb87fee2953a80b9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707471"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl (clase)
La `CMFCEditBrowseCtrl` clase admite el control de exploración de edición, que es un cuadro de texto editable que contiene opcionalmente un botón Examinar. Cuando el usuario hace clic en el botón Examinar, el control realiza una acción personalizada o muestra un cuadro de diálogo estándar que contiene un explorador de archivos o un explorador de carpetas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Constructor predeterminado.|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cmfceditbrowsectrl:: Enablebrowsebutton](#enablebrowsebutton)|Habilita o deshabilita (oculta) el botón Examinar.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Habilita el botón Examinar y coloca el control de exploración de edición en *Examinar archivo* modo.|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Habilita el botón Examinar y coloca el control de exploración de edición en *examinar carpetas* modo.|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Devuelve el modo de exploración actual.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Lo llama el marco de trabajo después de que el control de exploración de edición se actualiza con el resultado de una acción de exploración.|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Lo llama el marco de trabajo después de que el usuario hace clic en el botón Examinar.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Vuelve a dibujar el control de exploración de edición actual.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Lo llama el marco de trabajo para dibujar el botón Examinar.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Lo llama el marco de trabajo cuando se escribió un nombre de archivo no válido en el control de edición.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. Para obtener más información y la sintaxis, vea [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Establece una imagen personalizada para el botón Examinar.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice un control de edición Examinar para seleccionar un nombre de archivo o carpeta. Si lo desea, puede utilizar el control para realizar una acción personalizada, como se muestra un cuadro de diálogo. Puede mostrar o no mostrar el botón Examinar, y puede aplicar una etiqueta personalizada o una imagen en el botón.  
  
 El *modo de exploración* de la exploración de editar control determina si muestra un botón Examinar y qué acción se produce cuando se hace clic en el botón. Para obtener más información, consulte el [GetMode](#getmode) método.  
  
 La `CMFCEditBrowseCtrl` clase admite los modos siguientes.  
  
- **modo personalizado**

   Se realiza una acción personalizada cuando el usuario hace clic en el botón Examinar. Por ejemplo, puede mostrar un cuadro de diálogo específicos de la aplicación.  
  
- **modo de archivo**

   Cuando el usuario hace clic en el botón Examinar, se muestra un cuadro de diálogo de selección de archivos estándar.  
  
- **modo de carpeta**

   Cuando el usuario hace clic en el botón Examinar, se muestra un cuadro de diálogo de selección de carpeta estándar.  
  
## <a name="how-to-specify-an-edit-browse-control"></a>Cómo: Especificar un Control de exploración de edición  
 Realice los pasos siguientes para incorporar un control de exploración de edición en la aplicación:  
  
1.  Si desea implementar un modo de exploración personalizada, derive su propia clase de la `CMFCEditBrowseCtrl` clase y, a continuación, reemplace el [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) método. En el método reemplazado, ejecutar una acción de exploración personalizada y actualice el control de edición de exploración con el resultado.  
  
2.  Bien incrustar el `CMFCEditBrowseCtrl` objeto o el objeto de control de edición derivada examinar en el objeto de la ventana primaria.  
  
3.  Si usas el **Class Wizard** para crear un cuadro de diálogo, agregue un control de edición ( `CEdit`) para el formulario del cuadro de diálogo. Además, agregue una variable para tener acceso al control en el archivo de encabezado. En el archivo de encabezado, cambie el tipo de la variable de `CEdit` a `CMFCEditBrowseCtrl`. El control de edición de exploración se crearán automáticamente. Si no usa el **Class Wizard**, agregue un `CMFCEditBrowseCtrl` variable a su archivo de encabezado y, después, llame su `Create` método.  
  
4.  Si agrega un control de exploración de edición a un cuadro de diálogo, utilice el **ClassWizard** herramienta para configurar el intercambio de datos.  
  
5.  Llame a la [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), o [EnableBrowseButton](#enablebrowsebutton) método para establecer el modo de exploración y mostrar el botón Examinar. Llame a la [GetMode](#getmode) método para obtener el modo de exploración actual.  
  
6.  Para proporcionar una imagen personalizada para el botón Examinar, llame a la [SetBrowseButtonImage](#setbrowsebuttonimage) método o la invalidación del [OnDrawBrowseButton](#ondrawbrowsebutton) método.  
  
7.  Para quitar el botón Examinar desde el control de edición de exploración, llame a la [EnableBrowseButton](#enablebrowsebutton) método con el *bHabilitar el* parámetro establecido en FALSE.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar dos métodos en el `CMFCEditBrowseCtrl` clase: `EnableFolderBrowseButton` y `EnableFileBrowseButton`. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>  Cmfceditbrowsectrl:: Enablebrowsebutton  
 Muestra o no muestra el botón Examinar en el control de exploración de edición actual.  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>Parámetros  
 *bHabilitar el*  
 TRUE para mostrar el botón Examinar; Si es FALSE, no se muestre el botón Examinar. El valor predeterminado es TRUE.  
  
 *szLabel*  
 La etiqueta que se muestra en el botón Examinar. El valor predeterminado es " **...** ".  
  
### <a name="remarks"></a>Comentarios  
 Si el *bHabilitar el* parámetro es TRUE, implemente una acción personalizada para realizar cuando se hace clic en el botón Examinar. Para implementar una acción personalizada, derive una clase de la `CMFCEditBrowseCtrl` clase y, a continuación, invalide su [OnBrowse](#onbrowse) método.  
  
 Si el *bHabilitar el* parámetro es TRUE, el modo de exploración del control es `BrowseMode_Default`; en caso contrario, es el modo de exploración `BrowseMode_None`. Para obtener más información acerca de los modos de exploración, vea el [GetMode](#getmode) método.  
  
##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton  
 Muestra el botón Examinar en el control de exploración de edición actual y coloca el control en *Examinar archivo* modo.  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszDefExt*  
 Especifica la extensión de nombre de archivo predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es NULL.  
  
 *lpszFilter*  
 Especifica la cadena de filtro predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es NULL.  
  
 *dwFlags*  
 Marcas de cuadro de diálogo. El valor predeterminado es una combinación bit a bit (OR) de OFN_HIDEREADONLY y OFN_OVERWRITEPROMPT.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de cuadro de búsqueda modificable está en modo de búsqueda de archivo y el usuario hace clic en el botón Examinar, el control muestra el cuadro de diálogo de selección de archivos estándar.  
  
 Para obtener una lista completa de los indicadores disponibles, vea [estructura OPENFILENAME](/windows/desktop/api/commdlg/ns-commdlg-tagofna).  
  
##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 Muestra el botón Examinar en el control de exploración de edición actual y coloca el control en *examinar carpetas* modo.  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de edición de exploración está en modo de exploración de la carpeta y el usuario hace clic en el botón Examinar, el control muestra el cuadro de diálogo de selección de carpeta estándar.  
  
##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode  
 Recupera el modo de exploración del control de exploración de edición actual.  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores de enumeración que especifica el modo actual de la edición examinar control. El modo de exploración determina si el marco de trabajo muestra el botón Examinar y qué acción se produce cuando un usuario hace clic en ese botón.  
  
 La tabla siguiente muestra los valores devueltos posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`BrowseMode_Default`|**modo personalizado**. Se realiza una acción definida por el programador.|  
|`BrowseMode_File`|**modo de archivo**. Se muestra el cuadro de diálogo del explorador de archivos estándar.|  
|`BrowseMode_Folder`|**modo de carpeta**. Se muestra el cuadro de diálogo del explorador de carpetas estándar.|  
|`BrowseMode_None`|No se muestra el botón Examinar.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un `CMFCEditBrowseCtrl` objeto se inicializa en `BrowseMode_None` modo. Modificar el modo de exploración con el [cmfceditbrowsectrl:: Enablebrowsebutton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), y [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) métodos.  
  
##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate  
 Lo llama el marco de trabajo después de que el control de exploración de edición se actualiza con el resultado de una acción de exploración.  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar una acción personalizada.  
  
##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse  
 Lo llama el marco de trabajo después de que el usuario hace clic en el botón de examinar el control de edición Examinar.  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para ejecutar código personalizado cuando el usuario hace clic en el botón de examinar el control de edición Examinar. Derive su propia clase de la `CMFCEditBrowseCtrl` clase e invalidar sus `OnBrowse` método. En ese método, implemente una acción de exploración personalizada y, opcionalmente, actualice el cuadro de texto del control de edición Examinar. En la aplicación, use la [EnableBrowseButton](#enablebrowsebutton) método para colocar el control de exploración de edición en *exploración personalizada* modo.  
  
##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout  
 Vuelve a dibujar el control de exploración de edición actual.  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco llama a este método cuando el modo de exploración de la exploración de edición controlar los cambios. Para obtener más información, consulte [CMFCEditBrowseCtrl::GetMode](#getmode).  
  
##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton  
 Lo llama el marco de trabajo para dibujar el botón Examinar en el control de exploración de edición.  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Puntero a un contexto de dispositivo.  
  
 *Rect*  
 El rectángulo delimitador del botón Examinar.  
  
 *bIsButtonPressed*  
 TRUE si se presiona el botón; en caso contrario, FALSE.  
  
 *bIsButtonHot*  
 TRUE si el botón está resaltado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada para personalizar la apariencia del botón Examinar.  
  
##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage  
 Establece una imagen personalizada en el botón de examinar el control de edición Examinar.  
  
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
 *hIcon*  
 El identificador de un icono.  
  
 *hBitmap*  
 El identificador de un mapa de bits.  
  
 *uiBmpResId*  
 El identificador de recurso de un mapa de bits.  
  
 *bAutoDestroy*  
 TRUE para eliminar el icono especificado o el mapa de bits cuando se cierra este método; en caso contrario, FALSE. El valor predeterminado es TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para aplicar una imagen personalizada en el botón Examinar. De forma predeterminada, el marco de trabajo obtiene una imagen estándar cuando el control de edición de exploración está en *Examinar archivo* o *examinar carpetas* modo.  
  
##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName  
 Lo llama el marco de trabajo cuando se escribió un nombre de archivo no válido en el control de edición.  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 *strFileName*  
 Especifica el nombre de archivo no válido.  
  
### <a name="return-value"></a>Valor devuelto  
 Debe devolver FALSE si no se puede pasar el nombre de archivo con el cuadro de diálogo de archivo. En este caso, el foco se vuelve a establecer el control de edición y el usuario debe seguir editando. La implementación predeterminada, muestra un cuadro de mensaje que indica al usuario sobre el nombre de archivo no válido y devuelve FALSE. Puede invalidar este método, corrija el nombre de archivo y devolver TRUE para su posterior procesamiento.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
