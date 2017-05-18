---
title: Clase CMFCEditBrowseCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCEditBrowseCtrl::PreTranslateMessage method
- CMFCEditBrowseCtrl constructor
- CMFCEditBrowseCtrl class
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5c5650da677a442628049c9ef4b41c2142cfb2c2
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfceditbrowsectrl-class"></a>Clase CMFCEditBrowseCtrl
La `CMFCEditBrowseCtrl` clase es compatible con el control de exploración de edición, que es un cuadro de texto editable que contiene opcionalmente un botón Examinar. Cuando el usuario hace clic en el botón Examinar, el control realiza una acción personalizada o muestra un cuadro de diálogo estándar que contiene un explorador de archivos o un explorador de carpetas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Constructor predeterminado.|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Habilita o deshabilita (oculta) el botón Examinar.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Habilita el botón Examinar y coloca el control de exploración de edición en *Examinar archivo* modo.|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Habilita el botón Examinar y coloca el control de exploración de edición en *examinar carpetas* modo.|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Devuelve el modo de exploración actual.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Llamado por el marco de trabajo cuando el control de exploración de edición se actualiza con el resultado de una acción de exploración.|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón Examinar.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Vuelve a dibujar el control de exploración de edición actual.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Llamado por el marco para dibujar el botón Examinar.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Llamado por el marco de trabajo cuando se especificó un nombre de archivo no válido en el control de edición.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. Para obtener más información y la sintaxis, vea [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Establece una imagen personalizada para el botón Examinar.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice un control de exploración de edición para seleccionar un nombre de archivo o carpeta. Opcionalmente, puede utilizar el control para realizar una acción personalizada como para mostrar un cuadro de diálogo. Puede mostrar o no mostrar el botón Examinar, y puede aplicar una etiqueta personalizada o una imagen en el botón.  
  
 El *modo de exploración* de la exploración de editar control determina si muestra un botón de examinar y qué acción se produce cuando se hace clic en el botón. Para obtener más información, consulte el [GetMode](#getmode) método.  
  
 La `CMFCEditBrowseCtrl` clase admite los modos siguientes.  
  
 `custom mode`  
 Se realiza una acción personalizada cuando el usuario hace clic en el botón Examinar. Por ejemplo, puede mostrar un cuadro de diálogo específicos de la aplicación.  
  
 `file mode`  
 Cuando el usuario hace clic en el botón Examinar, se muestra un cuadro de diálogo de selección de archivos estándar.  
  
 `folder mode`  
 Cuando el usuario hace clic en el botón Examinar, se muestra un cuadro de diálogo de selección de carpeta estándar.  
  
## <a name="how-to-specify-an-edit-browse-control"></a>Cómo: Especificar un Control de exploración de edición  
 Realice los pasos siguientes para incorporar un control de exploración de edición en la aplicación:  
  
1.  Si desea implementar un modo de exploración personalizado, derive su propia clase de la `CMFCEditBrowseCtrl` de clase y, a continuación, reemplace el [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) método. En el método reemplazado, ejecutar una acción de exploración personalizada y actualice el control de exploración de edición con el resultado.  
  
2.  Incrustar en la `CMFCEditBrowseCtrl` objeto o el objeto de control de edición derivada examinar en el objeto de la ventana primaria.  
  
3.  Si utiliza la **Class Wizard** para crear un cuadro de diálogo, agregue un control de edición ( `CEdit`) para el formulario de cuadro de diálogo. Además, agregue una variable para tener acceso al control en el archivo de encabezado. En el archivo de encabezado, cambie el tipo de la variable de `CEdit` a `CMFCEditBrowseCtrl`. El control de exploración de edición se creará automáticamente. Si no utiliza la **Class Wizard**, agregar un `CMFCEditBrowseCtrl` variable a su archivo de encabezado y después llamar a su `Create` (método).  
  
4.  Si agrega un control de exploración de edición a un cuadro de diálogo, use la **ClassWizard** herramienta para configurar el intercambio de datos.  
  
5.  Llame a la [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), o [EnableBrowseButton](#enablebrowsebutton) método para establecer el modo de exploración y mostrar el botón Examinar. Llame a la [GetMode](#getmode) método para obtener el modo de exploración actual.  
  
6.  Para proporcionar una imagen personalizada para el botón Examinar, llame a la [SetBrowseButtonImage](#setbrowsebuttonimage) método o reemplazar el [OnDrawBrowseButton](#ondrawbrowsebutton) método.  
  
7.  Para quitar el control de exploración de editar el botón Examinar, llame a la [EnableBrowseButton](#enablebrowsebutton) método con la `bEnable` establecido en `FALSE`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar dos métodos en el `CMFCEditBrowseCtrl` clase: `EnableFolderBrowseButton` y `EnableFileBrowseButton`. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls Nº&6;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#7;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 Muestra o no mostrar el botón Examinar en el control de exploración de edición actual.  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 `TRUE`para mostrar el botón Examinar; `FALSE` no se muestre el botón Examinar. El valor predeterminado es `TRUE`.  
  
 `szLabel`  
 La etiqueta que se muestra en el botón Examinar. El valor predeterminado es " **... **".  
  
### <a name="remarks"></a>Comentarios  
 Si el `bEnable` parámetro es `TRUE`, implementar una acción personalizada para llevar a cabo cuando se hace clic en el botón Examinar. Para implementar una acción personalizada, derive una clase de la `CMFCEditBrowseCtrl` de clase y, a continuación, invalide su [OnBrowse](#onbrowse) método.  
  
 Si el `bEnable` parámetro es `TRUE`, es el modo de exploración del control `BrowseMode_Default`; en caso contrario, es el modo de exploración `BrowseMode_None`. Para obtener más información acerca de los modos de exploración, consulte la [GetMode](#getmode) método.  
  
##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 Muestra el botón Examinar en el control de exploración de edición actual y coloca el control en *Examinar archivo* modo.  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszDefExt`  
 Especifica la extensión de nombre de archivo predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es `NULL`.  
  
 `lpszFilter`  
 Especifica la cadena de filtro predeterminado que se usa en el cuadro de diálogo de selección de archivos. El valor predeterminado es `NULL`.  
  
 `dwFlags`  
 Marcas de cuadro de diálogo. El valor predeterminado es una combinación bit a bit (OR) de OFN_HIDEREADONLY y OFN_OVERWRITEPROMPT.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de cuadro de búsqueda modificable está en modo de búsqueda de archivo y el usuario hace clic en el botón Examinar, el control muestra el cuadro de diálogo de selección de archivos estándar.  
  
 Para obtener una lista completa de los indicadores disponibles, vea [estructura OPENFILENAME](https://msdn.microsoft.com/library/ms646839.aspx).  
  
##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 Muestra el botón Examinar en el control de exploración de edición actual y coloca el control en *examinar carpetas* modo.  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el control de exploración de edición está en modo de exploración de la carpeta y el usuario hace clic en el botón Examinar, el control muestra el cuadro de diálogo de selección de carpeta estándar.  
  
##  <a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 Recupera el modo de exploración del control de exploración de edición actual.  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores de enumeración que especifica el modo actual de la edición examinar control. El modo de exploración determina si el marco de trabajo muestra el botón Examinar y qué acción se produce cuando un usuario hace clic en ese botón.  
  
 La tabla siguiente muestra los valores devueltos posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`. Se realiza una acción definida por el programador.|  
|`BrowseMode_File`|`file mode`. Se muestra el cuadro de diálogo Explorador de archivos estándar.|  
|`BrowseMode_Folder`|`folder mode`. Se muestra el cuadro de diálogo del explorador de carpeta estándar.|  
|`BrowseMode_None`|No se muestra el botón Examinar.|  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un `CMFCEditBrowseCtrl` objeto se inicializa en `BrowseMode_None` modo. Modificar el modo de exploración con el [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), y [CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton) métodos.  
  
##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 Llamado por el marco de trabajo cuando el control de exploración de edición se actualiza con el resultado de una acción de exploración.  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar una acción personalizada.  
  
##  <a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 Lo llama el marco de trabajo después de que el usuario hace clic en el botón de examinar el control de edición Examinar.  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para ejecutar código personalizado cuando el usuario hace clic en el botón de examinar el control de edición Examinar. Derive su propia clase de la `CMFCEditBrowseCtrl` clase e invalidar su `OnBrowse` método. En ese método, implementar una acción de exploración personalizada y, opcionalmente, actualice el cuadro de texto del control de exploración de edición. En la aplicación, use la [EnableBrowseButton](#enablebrowsebutton) método para colocar el control de exploración de edición en *exploración personalizada* modo.  
  
##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 Vuelve a dibujar el control de exploración de edición actual.  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el modo de exploración de la exploración de edición del control cambios. Para obtener más información, consulte [CMFCEditBrowseCtrl::GetMode](#getmode).  
  
##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 Llamado por el marco para dibujar el botón Examinar en el control de exploración de edición.  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo.  
  
 `Rect`  
 El rectángulo delimitador del botón Examinar.  
  
 `bIsButtonPressed`  
 `TRUE`Si se presiona el botón; de lo contrario, `FALSE`.  
  
 `bIsButtonHot`  
 `TRUE`Si el botón está resaltado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada para personalizar la apariencia del botón Examinar.  
  
##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
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
 `hIcon`  
 El identificador de un icono.  
  
 `hBitmap`  
 El identificador de un mapa de bits.  
  
 `uiBmpResId`  
 El identificador de recurso de un mapa de bits.  
  
 `bAutoDestroy`  
 `TRUE`Para eliminar el icono especificado o un mapa de bits cuando este método finaliza; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para aplicar una imagen personalizada en el botón Examinar. De forma predeterminada, el marco de trabajo obtiene una imagen estándar cuando el control de exploración de edición que se encuentra en *Examinar archivo* o *examinar carpetas* modo.  
  
##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 Llamado por el marco de trabajo cuando se especificó un nombre de archivo no válido en el control de edición.  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `strFileName`  
 Especifica el nombre de archivo no válido.  
  
### <a name="return-value"></a>Valor devuelto  
 Debe devolver `FALSE` si el nombre de archivo no pueden pasarse más para el cuadro de diálogo de archivo. En este caso, el foco se vuelve a establecer el control de edición y el usuario debe seguir editando. La implementación predeterminada se muestra un cuadro de mensaje que indica al usuario sobre el nombre de archivo no válido y se devuelve `FALSE`. Puede invalidar este método, corrija el nombre de archivo y devolver `TRUE` para su posterior procesamiento.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

