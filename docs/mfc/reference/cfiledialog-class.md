---
title: Clase CFileDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileDialog
dev_langs:
- C++
helpviewer_keywords:
- CFileDialog class
- common file dialog boxes
- dialog boxes, common
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7cde10ee445a719bce6be4167698bd86c46a18c0
ms.lasthandoff: 02/24/2017

---
# <a name="cfiledialog-class"></a>CFileDialog (clase)
Encapsula el cuadro de diálogo común que se utiliza para abrir el archivo o las operaciones de guardar archivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileDialog::CFileDialog](#cfiledialog)|Construye un objeto `CFileDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileDialog::AddCheckButton](#addcheckbutton)|Agrega un botón de comprobación en el cuadro de diálogo.|  
|[CFileDialog::AddComboBox](#addcombobox)|Agrega un cuadro combinado en el cuadro de diálogo.|  
|[CFileDialog::AddControlItem](#addcontrolitem)|Agrega un elemento a un control contenedor en el cuadro de diálogo.|  
|[CFileDialog::AddEditBox](#addeditbox)|Agrega un cuadro de edición en el cuadro de diálogo.|  
|[CFileDialog::AddMenu](#addmenu)|Agrega un menú en el cuadro de diálogo.|  
|[CFileDialog::AddPlace](#addplace)|Sobrecargado. Agrega que una carpeta a la lista de plazas disponible para el usuario que abra o guarde los elementos.|  
|[CFileDialog::AddPushButton](#addpushbutton)|Agrega un botón en el cuadro de diálogo.|  
|[CFileDialog::AddRadioButtonList](#addradiobuttonlist)|Agrega un grupo de opciones (también conocido como botón de radio) en el cuadro de diálogo.|  
|[CFileDialog::AddSeparator](#addseparator)|Agrega un separador en el cuadro de diálogo.|  
|[CFileDialog::AddText](#addtext)|Agrega el contenido de texto en el cuadro de diálogo.|  
|[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)|Actualiza el estado de la `CFileDialog` para que coincida con los parámetros y marcadores almacenados en el `m_ofn` variable miembro.|  
|[CFileDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|  
|[CFileDialog::EnableOpenDropDown](#enableopendropdown)|Habilita una lista desplegable en el **abiertos** o **guardar** botón en el cuadro de diálogo.|  
|[CFileDialog::EndVisualGroup](#endvisualgroup)|Detiene la adición de elementos a un grupo visual en el cuadro de diálogo.|  
|[CFileDialog::GetCheckButtonState](#getcheckbuttonstate)|Obtiene el estado actual de un botón de comprobación (casilla de verificación) en el cuadro de diálogo.|  
|[CFileDialog::GetControlItemState](#getcontrolitemstate)|Obtiene el estado actual de un elemento de un control contenedor que se encuentra en el cuadro de diálogo.|  
|[CFileDialog::GetControlState](#getcontrolstate)|Obtiene la visibilidad actual y habilita los Estados de un control determinado.|  
|[CFileDialog::GetEditBoxText](#geteditboxtext)|Obtiene el texto actual en un control de cuadro de edición.|  
|[CFileDialog::GetFileExt](#getfileext)|Devuelve la extensión del archivo seleccionado.|  
|[CFileDialog:: GetFileName](#getfilename)|Devuelve el nombre de archivo del archivo seleccionado.|  
|[CFileDialog:: GetFileTitle](#getfiletitle)|Devuelve el título del archivo seleccionado.|  
|[CFileDialog::GetFolderPath](#getfolderpath)|Recupera la ruta de acceso del directorio o carpeta abierta para un tipo de explorador **abrir** o **Guardar como** cuadro de diálogo común.|  
|[CFileDialog::GetIFileDialogCustomize](#getifiledialogcustomize)|Recupera el objeto COM interno para una personalizada `CFileDialog` objeto.|  
|[CFileDialog::GetIFileOpenDialog](#getifileopendialog)|Recupera el objeto COM interno para una `CFileDialog` que se utiliza como un **abiertos** cuadro de diálogo de archivo.|  
|[CFileDialog::GetIFileSaveDialog](#getifilesavedialog)|Recupera el objeto COM interno para una `CFileDialog` que se utiliza como un **guardar** cuadro de diálogo de archivo.|  
|[CFileDialog::GetNextPathName](#getnextpathname)|Devuelve la ruta de acceso completa del archivo seleccionado siguiente.|  
|[CFileDialog::GetOFN](#getofn)|Recupera el `OPENFILENAME` estructura de la `CFileDialog` objeto.|  
|[CFileDialog::GetPathName](#getpathname)|Devuelve la ruta de acceso completa del archivo seleccionado.|  
|[CFileDialog::GetReadOnlyPref](#getreadonlypref)|Devuelve el estado de sólo lectura del archivo seleccionado.|  
|[CFileDialog::GetResult](#getresult)|Obtiene la opción realizados por el usuario en el cuadro de diálogo.|  
|[CFileDialog::GetResults](#getresults)|Obtiene las opciones del usuario en un cuadro de diálogo que permite la selección múltiple.|  
|[CFileDialog::GetSelectedControlItem](#getselectedcontrolitem)|Obtiene un elemento determinado de controles del contenedor especificado en el cuadro de diálogo.|  
|[CFileDialog::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento de la lista de nombres de archivo.|  
|[CFileDialog::HideControl](#hidecontrol)|Oculta el control especificado en un tipo de explorador **abiertos** o **Guardar como** cuadro de diálogo común.|  
|[CFileDialog::IsPickFoldersMode](#ispickfoldersmode)|Determina si el cuadro de diálogo actual en modo de selector de carpetas.|  
|[CFileDialog::MakeProminent](#makeprominent)|Sitios de un control en el cuadro de diálogo para que destaque en comparación con otros controles agregados.|  
|[CFileDialog::RemoveControlItem](#removecontrolitem)|Quita un elemento de un control contenedor en el cuadro de diálogo.|  
|[CFileDialog::SetCheckButtonState](#setcheckbuttonstate)|Establece el estado actual de un botón de comprobación (casilla de verificación) en el cuadro de diálogo.|  
|[CFileDialog::SetControlItemState](#setcontrolitemstate)|Establece el estado actual de un elemento en un control contenedor que se encuentra en el cuadro de diálogo.|  
|[CFileDialog::SetControlItemText](#setcontrolitemtext)|Establece el texto de un elemento del control. Por ejemplo, el texto que acompaña a un elemento en un menú o un botón de radio.|  
|[CFileDialog::SetControlLabel](#setcontrollabel)|Establece el texto asociado a un control, como el texto del botón o una etiqueta de cuadro de edición.|  
|[CFileDialog::SetControlState](#setcontrolstate)|Establece la visibilidad actual y habilita los Estados de un control determinado.|  
|[CFileDialog::SetControlText](#setcontroltext)|Establece el texto para el control especificado en un tipo de explorador **abiertos** o **Guardar como** cuadro de diálogo común.|  
|[CFileDialog::SetDefExt](#setdefext)|Establece la extensión de nombre de archivo predeterminado para un tipo de explorador **abiertos** o **Guardar como** cuadro de diálogo común.|  
|[CFileDialog::SetEditBoxText](#seteditboxtext)|Establece el texto actual en un control de cuadro de edición.|  
|[CFileDialog::SetProperties](#setproperties)|Proporciona un almacén de propiedades que define los valores predeterminados que se van a usar para el elemento que se está guardando.|  
|[CFileDialog::SetSelectedControlItem](#setselectedcontrolitem)|Establece el estado seleccionado de un elemento determinado en un grupo de botones de opción o un cuadro combinado que se encuentra en el cuadro de diálogo.|  
|[CFileDialog::SetTemplate](#settemplate)|Establece la plantilla de cuadro de diálogo para el `CFileDialog` objeto.|  
|[CFileDialog::StartVisualGroup](#startvisualgroup)|Declara un grupo visual en el cuadro de diálogo. Las llamadas subsiguientes a cualquier método "add" agregan esos elementos a este grupo.|  
|[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)|Actualiza los datos almacenados en el `m_ofn` la variable miembro que coinciden con el estado actual del cuadro de diálogo de archivo.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileDialog::OnButtonClicked](#onbuttonclicked)|Se llama cuando se hace clic en el botón.|  
|[CFileDialog::OnCheckButtonToggled](#oncheckbuttontoggled)|Se llama cuando la casilla está activada o desactivada.|  
|[CFileDialog::OnControlActivating](#oncontrolactivating)|Llamado cuando se activa el control.|  
|[CFileDialog::OnFileNameChange](#onfilenamechange)|Controla el `WM_NOTIFY CDN_SELCHANGE` mensaje.|  
|[CFileDialog::OnFileNameOK](#onfilenameok)|Valida el nombre de archivo especificado en el cuadro de diálogo.|  
|[CFileDialog::OnFolderChange](#onfolderchange)|Controla el `WM_NOTIFY CDN_FOLDERCHANGE` mensaje.|  
|[CFileDialog::OnInitDone](#oninitdone)|Controla el `WM_NOTIFY CDN_INITDONE` mensaje.|  
|[CFileDialog::OnItemSelected](#onitemselected)|Se llama cuando se selecciona el elemento contenedor.|  
|[CFileDialog::OnLBSelChangedNotify](#onlbselchangednotify)|Le permite realizar acciones personalizadas cuando cambia la selección de archivo.|  
|[CFileDialog::OnShareViolation](#onshareviolation)|Identificadores de compartan infracciones.|  
|[CFileDialog::OnTypeChange](#ontypechange)|Controla el `WM_NOTIFY CDN_TYPECHANGE` mensaje.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFileDialog::m_ofn](#m_ofn)|Windows `OPENFILENAME` estructura. Proporciona acceso a los parámetros de cuadro de diálogo de archivo básico.|  
  
## <a name="remarks"></a>Comentarios  
 Cuadros de diálogo comunes permiten implementar los cuadros de diálogo de selección de archivos, por ejemplo, **abrir archivo** y **Guardar como**, de manera que sea coherente con los estándares de Windows.  
  
 Puede usar `CFileDialog` tal cual con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CFileDialog` y escribir un constructor para satisfacer sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo MFC estándar, ya que se derivan de la [CCommonDialog clase](../../mfc/reference/ccommondialog-class.md). `CFileDialog`se basa en el COMMDLG. Archivo DLL que se incluye en Windows.  
  
 La apariencia y la funcionalidad de la `CFileDialog` con [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] difieren de las versiones anteriores de Windows. El valor predeterminado `CFileDialog` utiliza automáticamente el nuevo [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] estilo sin cambios en el código si se compila un programa y ejecución en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Utilice la `bVistaStyle` parámetro en el constructor para reemplazar manualmente esta actualización automática. La excepción a la actualización automática es cuadros de diálogo personalizados. No se convertirán al nuevo estilo. Para obtener más información sobre el constructor, consulte [CFileDialog::CFileDialog](#cfiledialog).  
  
> [!NOTE]
>  El sistema de Id. de control difiere en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] desde versiones anteriores de Windows cuando se usa un `CFileDialog`. Debe actualizar todas las referencias a `CFileDialog` controles en el código antes de que puede portar el proyecto desde una versión anterior de Windows.  
  
 Algunos `CFileDialog` métodos no son compatibles con [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Consulte el tema del método individuales para obtener información sobre si se admite el método. Además, no se admiten las siguientes funciones heredadas en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)  
  
- [CDialog::OnSetFont](../../mfc/reference/cdialog-class.md#onsetfont)  
  
 Los mensajes de windows para la `CFileDialog` clase varían en función de qué sistema operativo que está utilizando. Por ejemplo, Windows XP no admite [CDialog::OnCancel](../../mfc/reference/cdialog-class.md#oncancel) y [CDialog::OnOK](../../mfc/reference/cdialog-class.md#onok) para el `CFileDialog` clase. Sin embargo, [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] es compatible con ellos. Para obtener más información acerca de los mensajes que se generan y el orden en que se reciben, consulte [ejemplo CFileDialog: orden de eventos de registro](../../visual-cpp-samples.md).  
  
 Para usar un `CFileDialog` , primero cree el objeto utilizando la `CFileDialog` constructor. Una vez construido el cuadro de diálogo, puede establecer o modificar los valores de la [CFileDialog::m_ofn](#m_ofn) estructura para inicializar los valores o los Estados de los controles de cuadro de diálogo. El `m_ofn` estructura es de tipo `OPENFILENAME`. Para obtener más información, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Después de inicializar los controles de cuadro de diálogo, llame a la [CFileDialog::DoModal](#domodal) cuadro de método para mostrar el cuadro de diálogo para que el usuario puede escribir la ruta de acceso y nombre de archivo. `DoModal`Devuelve si el usuario hace clic en Aceptar (IDOK) o en el botón Cancelar (IDCANCEL). Si `DoModal` devuelve IDOK, puede utilizar uno de los `CFileDialog` funciones miembro públicas para recuperar la información se colocan en el usuario.  
  
> [!NOTE]
>  En [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], varias llamadas a [IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980) se produce un error. La segunda llamada a `SetFileTypes` para cualquier instancia de un `CFileDialog` devolverá `E_UNEXPECTED` en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Algunos `CFileDialog` método aquellas funciones que llaman a `SetFileTypes`. Por ejemplo, dos llamadas a `CFileDialog::DoModal` para la misma instancia de un `CFileDialog` genera [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c).  
  
 `CFileDialog`incluye varios miembros protegidos que permiten realizar un control personalizado de infracciones de recurso compartido, validación de nombre de archivo y la notificación de cambio de cuadro de lista. Estos miembros protegidos son funciones de devolución de llamada que no es necesario que la mayoría de las aplicaciones usar porque control predeterminados se realiza automáticamente. Las entradas de mapa de mensajes para estas funciones no son necesarias porque son funciones virtuales estándares.  
  
 Puede utilizar las ventanas [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  
  
 La destrucción de `CFileDialog` objetos se controla automáticamente. No es necesario llamar a [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog).  
  
 Para permitir al usuario seleccionar varios archivos, establecer el `OFN_ALLOWMULTISELECT` marca antes de llamar a `DoModal`. Debe proporcionar su propio búfer de nombre de archivo para dar cabida a la lista de varios nombres de archivo. Esto se hace reemplazando `m_ofn.lpstrFile` con un puntero a un búfer ha asignado, después de construir la `CFileDialog`, pero antes de llamar a `DoModal`.  
  
 Además, debe establecer `m_ofn.nMaxFile` con el número de caracteres en el búfer señalado por `m_ofn.lpstrFile`. Si establece el número máximo de archivos que se van a seleccionar para `n`, el tamaño de búfer necesario es `n * (_MAX_PATH + 1) + 1`. El primer elemento que se devuelve en el búfer es la ruta de acceso a la carpeta donde se han seleccionado los archivos. Para [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]-cuadros de diálogo de estilo, las cadenas de nombre de archivo y directorio están terminada en null, con un carácter null adicional tras el último nombre de archivo. Este formato permite que los cuadros de diálogo de tipo de explorador devolver los nombres de archivo largos que incluyen espacios. Cuadros de diálogo de estilo antiguo, las cadenas de nombre de archivo y directorio están separadas por espacios y la función utiliza nombres de archivo cortos para los nombres de archivo con espacios.  
  
 En el ejemplo siguiente se muestra cómo utilizar un búfer para recuperar y mostrar varios nombres de archivo.  
  
 [!code-cpp[23 de NVC_MFCFiles #](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 Para cambiar el tamaño del búfer de respuesta al usuario seleccionar varios nombres de archivo, debe derivar una nueva clase de `CFileDialog` e invalidar la [CFileDialog::OnFileNameChange](#onfilenamechange) método.  
  
 Si deriva una nueva clase de `CFileDialog`, puede utilizar un mapa de mensajes para controlar los mensajes. Para extender el control de mensajes de forma predeterminada, derive una clase de `CFileDialog`, agregar un mapa de mensajes a la nueva clase y proporcionan funciones miembro para los mensajes nuevos. No es necesario proporcionar una función de enlace para personalizar el cuadro de diálogo.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CFileDialog`, proporcionan una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Pasar los mensajes sin procesar a la clase base. No es necesario personalizar la función de enlace.  
  
 Cuando se utiliza la [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] estilo de la `CFileDialog`, no puede utilizar mapas de mensajes y plantillas de cuadro de diálogo. En su lugar, debe utilizar las interfaces COM para una funcionalidad similar.  
  
 Para obtener más información acerca de cómo usar `CFileDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdlgs.h  
  
##  <a name="a-nameaddcheckbuttona--cfiledialogaddcheckbutton"></a><a name="addcheckbutton"></a>CFileDialog::AddCheckButton  
 Agrega un botón de comprobación en el cuadro de diálogo.  
  
```  
HRESULT AddCheckButton(
    DWORD dwIDCtl,  
    const CString& strLabel,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del botón de comprobación para agregar.  
  
 `strLabel`  
 El nombre del botón de comprobación.  
  
 `bChecked`  
 Un valor booleano que indica el estado actual del botón de comprobación. `TRUE`Si está activado; `FALSE` lo contrario  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddcomboboxa--cfiledialogaddcombobox"></a><a name="addcombobox"></a>CFileDialog::AddComboBox  
 Agrega un cuadro combinado en el cuadro de diálogo.  
  
```  
HRESULT AddComboBox(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del cuadro combinado para agregar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddcontrolitema--cfiledialogaddcontrolitem"></a><a name="addcontrolitem"></a>CFileDialog::AddControlItem  
 Agrega un elemento a un control contenedor en el cuadro de diálogo.  
  
```  
HRESULT AddControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor para agregar el elemento.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
 `strLabel`  
 Texto del elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddeditboxa--cfiledialogaddeditbox"></a><a name="addeditbox"></a>CFileDialog::AddEditBox  
 Agrega un cuadro de edición en el cuadro de diálogo.  
  
```  
HRESULT AddEditBox(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 Id. del cuadro de edición para agregar.  
  
 `strText`  
 El nombre del cuadro de edición.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddmenua--cfiledialogaddmenu"></a><a name="addmenu"></a>CFileDialog::AddMenu  
 Agrega un menú en el cuadro de diálogo.  
  
```  
HRESULT AddMenu(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del menú Agregar.  
  
 `strLabel`  
 El nombre del menú.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddplacea--cfiledialogaddplace"></a><a name="addplace"></a>CFileDialog::AddPlace  
 Agrega que una carpeta a la lista de plazas disponible para el usuario que abra o guarde los elementos.  
  
```  
void AddPlace(
    LPCWSTR lpszFolder,  
    FDAP fdap = FDAP_TOP) throw();

 
void AddPlace(
    IShellItem* psi,  
    FDAP fdap = FDAP_TOP) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFolder`  
 Ruta de acceso a la carpeta debe estar disponible para el usuario. Sólo puede ser una carpeta.  
  
 `fdap`  
 Especifica dónde se coloca la carpeta en la lista.  
  
 `psi`  
 Puntero a un IShellItem que representa la carpeta debe estar disponible para el usuario. Sólo puede ser una carpeta.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddpushbuttona--cfiledialogaddpushbutton"></a><a name="addpushbutton"></a>CFileDialog::AddPushButton  
 Agrega un botón en el cuadro de diálogo.  
  
```  
HRESULT AddPushButton(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del botón Agregar.  
  
 `strLabel`  
 El nombre del botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddradiobuttonlista--cfiledialogaddradiobuttonlist"></a><a name="addradiobuttonlist"></a>CFileDialog::AddRadioButtonList  
 Agrega un grupo de opciones (también conocido como botón de radio) en el cuadro de diálogo.  
  
```  
HRESULT AddRadioButtonList(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 Id. del grupo de botones de opción para agregar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddseparatora--cfiledialogaddseparator"></a><a name="addseparator"></a>CFileDialog::AddSeparator  
 Agrega un separador en el cuadro de diálogo.  
  
```  
HRESULT AddSeparator(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 Agregue el identificador del separador.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddtexta--cfiledialogaddtext"></a><a name="addtext"></a>CFileDialog::AddText  
 Agrega texto al cuadro de diálogo.  
  
```  
HRESULT AddText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 Identificador del texto que se agrega.  
  
 `strText`  
 El nombre de texto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameapplyofntoshelldialoga--cfiledialogapplyofntoshelldialog"></a><a name="applyofntoshelldialog"></a>CFileDialog::ApplyOFNToShellDialog  
 Actualiza el estado actual de la [CFileDialog](../../mfc/reference/cfiledialog-class.md) basándose en los valores almacenados en el `m_ofn` estructura de datos.  
  
```  
void ApplyOFNToShellDialog();
```  
  
### <a name="remarks"></a>Comentarios  
 En las versiones de Windows anteriores a [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], el miembro [OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx) estructura de datos se sincroniza continuamente con el estado de la `CFileDialog`. Los cambios realizados en el [m_ofn](#m_ofn) variable miembro se reflejan inmediatamente en el estado del cuadro de diálogo. Además, cualquier cambio en el estado del cuadro de diálogo actualiza inmediatamente el `m_ofn` variable miembro.  
  
 En [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], los valores de la `m_ofn` variable miembro y el estado de la `CFileDialog` no se garantiza que se sincronizarán. Esta función fuerza el estado de la `CFileDialog` actualizarse para que coincida con el `m_ofn` estructura. Windows llama a esta función automáticamente durante la [CFileDialog::DoModal](#domodal).  
  
 Para obtener más información acerca de cómo utilizar el `CFileDialog` en la clase [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], consulte [clase CFileDialog](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog).  
  
##  <a name="a-namecfiledialoga--cfiledialogcfiledialog"></a><a name="cfiledialog"></a>CFileDialog::CFileDialog  
 Llame a esta función para construir un cuadro de diálogo de archivo estándar de Windows.  
  
```  
explicit CFileDialog(
    BOOL bOpenFileDialog,  
    LPCTSTR lpszDefExt = NULL,  
    LPCTSTR lpszFileName = NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter = NULL,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0,  
    BOOL bVistaStyle = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bOpenFileDialog`  
 El parámetro que especifica qué tipo de cuadro de diálogo para crear. Establézcalo en `TRUE` para construir un **abrir archivo** cuadro de diálogo. Establézcalo en `FALSE` para construir un **Guardar como** cuadro de diálogo.  
  
 [in] `lpszDefExt`  
 Extensión predeterminada de nombre de archivo. Si el usuario no tiene una extensión conocida (aquel que tiene una asociación en el equipo del usuario) en el cuadro Nombre de archivo, la extensión especificada por `lpszDefExt` se anexa automáticamente al nombre de archivo. Si este parámetro es `NULL`, se anexa ninguna extensión.  
  
 [in] `lpszFileName`  
 El nombre de archivo inicial que aparece en el cuadro Nombre de archivo. Si `NULL`, no aparece ningún nombre de archivo inicial.  
  
 [in] `dwFlags`  
 Una combinación de uno o más marcadores que puede usar para personalizar el cuadro de diálogo. Para obtener una descripción de estas marcas, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si modifica el `m_ofn.Flags` miembros de estructura, utilice un operador OR bit a bit de los cambios mantener intacto el comportamiento predeterminado.  
  
 [in] `lpszFilter`  
 Una serie de pares de cadenas que especifican filtros puede aplicar al archivo. Si especifica filtros de archivos, sólo los archivos que coinciden con los criterios de filtro aparecerán en la lista de archivos. Vea la sección Comentarios para obtener más información acerca de cómo trabajar con filtros de archivos.  
  
 [in] `pParentWnd`  
 Puntero a la ventana primaria o propietaria del cuadro de diálogo de archivo.  
  
 [in] `dwSize`  
 El tamaño de la `OPENFILENAME` estructura. Este valor depende de la versión del sistema operativo. MFC utiliza este parámetro para determinar el tipo apropiado de cuadro de diálogo Crear (por ejemplo, new [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] cuadros de diálogo en lugar de cuadros de diálogo de NT4). El tamaño predeterminado de 0 significa que el código MFC determinan el tamaño del cuadro de diálogo correctos para utilizar según la versión de sistema operativo en el que se ejecuta el programa.  
  
 [in] `bVistaStyle`  
 **Nota** este parámetro está disponible en Visual Studio 2008 y versiones posteriores y será que el cuadro de diálogo nuevo estilo que se utilizará sólo si se está ejecutando en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] o posterior.  
  
 El parámetro que especifica el estilo del cuadro de diálogo de archivo. Establézcalo en `TRUE` para utilizar los nuevos diálogos de archivo de estilo de Vista. De lo contrario, se utilizará el estilo anterior de cuadros de diálogo. Vea la sección Comentarios para obtener más información acerca de ejecución en la Vista.  
  
### <a name="remarks"></a>Comentarios  
 Ya sea un **abrir archivo** o **Guardar como** se construye el cuadro de diálogo, dependiendo del valor de `bOpenFileDialog`.  
  
 Especificar una extensión predeterminada con `lpszDefExt` no se puede producir el comportamiento que espera, ya que rara vez es predecible qué extensiones tienen asociaciones de archivo en el equipo del usuario. Si necesita más control sobre la incorporación de una extensión de forma predeterminada, puede derivar su propia clase de `CFileDialog`e invalidar el `CFileDialog::OnFileNameOK` método para realizar su propio control de extensión.  
  
 Para permitir al usuario seleccionar varios archivos, establezca la `OFN_ALLOWMULTISELECT` marca antes de llamar a [DoModal](#domodal). Debe proporcionar su propio búfer de nombre de archivo para almacenar la lista de varios nombres de archivo. Esto se hace reemplazando `m_ofn.lpstrFile` con un puntero a un búfer ha asignado, después de construir la [CFileDialog](../../mfc/reference/cfiledialog-class.md), pero antes de llamar a `DoModal`. Además, debe establecer `m_ofn.nMaxFile` con el número de caracteres en el búfer señalado por `m_ofn.lpstrFile`. Si establece el número máximo de archivos que se van a seleccionar para `n`, el tamaño de búfer necesario es `n`*(_MAX_PATH + 1) + 1. Por ejemplo:  
  
 [!code-cpp[23 de NVC_MFCFiles #](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 Para permitir al usuario cambiar el tamaño de un cuadro de diálogo de tipo explorador con el mouse o el teclado, establezca el `OFN_ENABLESIZING` marca. Establecer este indicador solo es necesario si se proporciona un procedimiento de enlace o la plantilla personalizada. La marca sólo funciona con un cuadro de diálogo tipo de explorador; cuadros de diálogo de estilo antiguo no puede cambiarse.  
  
 El `lpszFilter` parámetro se utiliza para determinar el tipo de nombre de archivo debe tener un archivo que se mostrará en la lista de archivos. La primera cadena en el par de cadenas describe el filtro; la segunda cadena indica la extensión de nombre de archivo para usar. Varias extensiones pueden especificarse mediante un punto y coma (el carácter ';') como delimitador. La cadena finaliza con dos ' |' caracteres, seguidos por un `NULL` caracteres. También puede utilizar un [CString](../../atl-mfc-shared/using-cstring.md) objeto para este parámetro.  
  
 Por ejemplo, [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] permite a los usuarios abrir archivos que tienen extensiones .xlc (gráfico) o xls (hoja de cálculo), entre otros. El filtro de Excel podría escribirse como:  
  
 [!code-cpp[NVC_MFCFiles&#24;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_2.cpp)]  
  
 Sin embargo, si piensa utilizar esta cadena directamente al actualizar el `OPENFILENAME` estructura, debe delimitar las cadenas con el carácter null, '\0', en lugar de las barras verticales ('| ').  
  
 El `bVistaStyle` parámetro solo es aplicable cuando ejecuta bajo [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. En versiones anteriores de Windows, este parámetro se ignora. Si `bVistaStyle` está establecido en `TRUE`, cuando se compila un programa con [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] o posterior, el nuevo estilo de Vista **cuadro de diálogo archivo** se usará. De lo contrario, el estilo anterior de MFC **cuadro de diálogo archivo** se usará.  
  
 Plantillas de cuadro de diálogo no se admiten en los cuadros de diálogo basados en`bVistaStyle`  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFileDialog::DoModal](#domodal).  
  
##  <a name="a-namedomodala--cfiledialogdomodal"></a><a name="domodal"></a>CFileDialog::DoModal  
 Llame a esta función para mostrar el cuadro de diálogo de archivos comunes de Windows y permitir al usuario explorar los archivos y directorios y escriba un nombre de archivo.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **IDOK** o **IDCANCEL**. Si **IDCANCEL** es devuelto, llame a Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error.  
  
 **IDOK** y **IDCANCEL** son constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.  
  
### <a name="remarks"></a>Comentarios  
 Si desea inicializar las distintas opciones del cuadro de diálogo de archivo estableciendo los miembros de la **m_ofn** estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.  
  
 Por ejemplo, si desea permitir al usuario seleccionar varios archivos, establecer el `OFN_ALLOWMULTISELECT` marca antes de llamar a `DoModal`, como se muestra en el ejemplo de código de este tema.  
  
 Cuando el usuario hace clic en los botones Aceptar o cancelar el cuadro de diálogo o selecciona el cierre de opción en el cuadro de diálogo control de menú, el control se devuelve a la aplicación. A continuación, puede llamar otras funciones miembro para recuperar la configuración o la información de las entradas de usuario en el cuadro de diálogo.  
  
 `DoModal`es una función virtual invalida desde la clase `CDialog`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCFiles&#25;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_3.cpp)]  
  
##  <a name="a-nameenableopendropdowna--cfiledialogenableopendropdown"></a><a name="enableopendropdown"></a>CFileDialog::EnableOpenDropDown  
 Habilita una lista desplegable al abrir o guardar el botón en el cuadro de diálogo.  
  
```  
HRESULT EnableOpenDropDown(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador de la lista desplegable.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameendvisualgroupa--cfiledialogendvisualgroup"></a><a name="endvisualgroup"></a>CFileDialog::EndVisualGroup  
 Detiene la adición de elementos a un grupo visual en el cuadro de diálogo.  
  
```  
HRESULT EndVisualGroup();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si es correcto; un valor de error en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcheckbuttonstatea--cfiledialoggetcheckbuttonstate"></a><a name="getcheckbuttonstate"></a>CFileDialog::GetCheckButtonState  
 Recupera el estado actual de un botón de comprobación (casilla de verificación) en el cuadro de diálogo.  
  
```  
HRESULT GetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL& bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador de la casilla de verificación.  
  
 `bChecked`  
 El estado de la casilla de verificación. `TRUE`indica comprobado; `FALSE` indica desactivada.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcontrolitemstatea--cfiledialoggetcontrolitemstate"></a><a name="getcontrolitemstate"></a>CFileDialog::GetControlItemState  
 Recupera el estado actual de un elemento de un control contenedor que se encuentra en el cuadro de diálogo.  
  
```  
HRESULT GetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
 `dwState`  
 Una referencia a una variable que recibe uno de varios valores de la enumeración CDCONTROLSTATE que indica el estado actual del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcontrolstatea--cfiledialoggetcontrolstate"></a><a name="getcontrolstate"></a>CFileDialog::GetControlState  
 Recupera la visibilidad actual y habilita los Estados de un control determinado.  
  
```  
HRESULT GetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control.  
  
 `dwState`  
 Una referencia a una variable que recibe uno o más valores de la enumeración CDCONTROLSTATE que indica el estado actual del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegeteditboxtexta--cfiledialoggeteditboxtext"></a><a name="geteditboxtext"></a>CFileDialog::GetEditBoxText  
 Recupera el texto actual en un control de cuadro de edición.  
  
```  
HRESULT GetEditBoxText(
    DWORD dwIDCtl,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del cuadro de edición.  
  
 `strText`  
 Valor de texto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetfileexta--cfiledialoggetfileext"></a><a name="getfileext"></a>CFileDialog::GetFileExt  
 Llame a esta función para recuperar la extensión del nombre de archivo especificado en el cuadro de diálogo.  
  
```  
CString GetFileExt() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La extensión del nombre de archivo.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si el nombre del archivo introducido datos. TXT, `GetFileExt` devuelve "TXT".  
  
 Si `m_ofn.Flags` tiene la `OFN_ALLOWMULTISELECT` indicador establecido, esta cadena contiene una secuencia de cadenas terminadas en null, con la primera cadena que se va a la ruta del directorio del grupo de archivos seleccionado, seguido por los nombres de todos los archivos seleccionados por el usuario. Para recuperar rutas de acceso de archivo, use la [GetStartPosition](#getstartposition) y [GetNextPathName](#getnextpathname) funciones miembro.  
  
##  <a name="a-namegetfilenamea--cfiledialoggetfilename"></a><a name="getfilename"></a>CFileDialog:: GetFileName  
 Llame a esta función para recuperar el nombre del nombre de archivo especificado en el cuadro de diálogo.  
  
```  
CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre del archivo.  
  
### <a name="remarks"></a>Comentarios  
 El nombre del archivo incluye el prefijo y la extensión. Por ejemplo, `GetFileName` devolverá "TEXT. DAT"para el archivo C:\FILES\TEXT.DAT.  
  
 Si `m_ofn.Flags` tiene la `OFN_ALLOWMULTISELECT` marcador establecido, se debe llamar a [GetHeadPosition](#getstartposition) y [GetNextPathName](#getnextpathname) para recuperar una ruta de acceso de archivo.  
  
##  <a name="a-namegetfiletitlea--cfiledialoggetfiletitle"></a><a name="getfiletitle"></a>CFileDialog:: GetFileTitle  
 Llame a esta función para recuperar el título del archivo especificado en el cuadro de diálogo.  
  
```  
CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El título del archivo.  
  
### <a name="remarks"></a>Comentarios  
 El título del archivo incluye sólo su prefijo, sin la ruta de acceso o la extensión. Por ejemplo, `GetFileTitle` devolverá "TEXT" para el archivo C:\FILES\TEXT.DAT.  
  
 Si `m_ofn.Flags` tiene la `OFN_ALLOWMULTISELECT` indicador establecido, esta cadena contiene una secuencia de cadenas terminadas en null, con la primera cadena que se va a la ruta del directorio del grupo de archivos seleccionado, seguido por los nombres de todos los archivos seleccionados por el usuario. Por este motivo, utilice la [GetStartPosition](#getstartposition) y [GetNextPathName](#getnextpathname) funciones miembro para recuperar el siguiente nombre de archivo en la lista.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFileDialog::DoModal](#domodal).  
  
##  <a name="a-namegetfolderpatha--cfiledialoggetfolderpath"></a><a name="getfolderpath"></a>CFileDialog::GetFolderPath  
 Llame a esta función miembro para recuperar la ruta de acceso de la carpeta abierta o directorio para un cuadro de diálogo común de estilo explorador abrir o guardar como.  
  
```  
CString GetFolderPath() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene la carpeta abierta o directorio.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo se debe haber creado con el **OFN_EXPLORER** estilo; de lo contrario, el método producirá una aserción.  
  
 Puede llamar a este método solo mientras se muestra el cuadro de diálogo. Después de cerrar el cuadro de diálogo, esta función ya no funcionará y el método generará un error con una aserción.  
  
##  <a name="a-namegetifiledialogcustomizea--cfiledialoggetifiledialogcustomize"></a><a name="getifiledialogcustomize"></a>CFileDialog::GetIFileDialogCustomize  
 Recupera un puntero al objeto COM para un determinado [CFileDialog](../../mfc/reference/cfiledialog-class.md).  
  
```  
IFileDialogCustomize* GetIFileDialogCustomize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero al objeto COM para el `CFileDialog`. Es su responsabilidad para liberar el puntero this adecuadamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función sólo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] con un objeto que tiene `bVistaStyle` establecido en `true`. Si utiliza esta función cuando `bVistaStyle` es `false`, devolverá `NULL` en modo de lanzamiento y produce una aserción en modo de depuración.  
  
 Para obtener más información acerca de la `IFileDialogCustomize` , vea [IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo recupera el objeto COM interno. Para ejecutar este ejemplo de código, debe compilarlo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog Nº&4;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_4.cpp)]  
  
##  <a name="a-namegetifileopendialoga--cfiledialoggetifileopendialog"></a><a name="getifileopendialog"></a>CFileDialog::GetIFileOpenDialog  
 Recupera un puntero al objeto COM para un determinado `CFileDialog`.  
  
```  
IFileOpenDialog* GetIFileOpenDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero al objeto COM para el `CFileDialog`. Es su responsabilidad para liberar el puntero this adecuadamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función sólo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] con un objeto que tiene `bVistaStyle` establecido en `true`. Esta función devuelve `NULL` si la `CFileDialog` no es un **abiertos** cuadro de diálogo o si `bVistaStyle` está establecido en `false`. En este último caso, la función sólo devuelve `NULL` en modo de lanzamiento - en modo de depuración producirá una aserción.  
  
 Para obtener más información acerca de la `IFileOpenDialog` , vea [IFileOpenDialog](http://msdn.microsoft.com/library/windows/desktop/bb775834).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo recupera el objeto COM interno. Para ejecutar este código, debe compilarlo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog&#2;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_5.cpp)]  
  
##  <a name="a-namegetifilesavedialoga--cfiledialoggetifilesavedialog"></a><a name="getifilesavedialog"></a>CFileDialog::GetIFileSaveDialog  
 Recupera un puntero al objeto COM para un determinado `CFileDialog`.  
  
```  
IFileSaveDialog* GetIFileSaveDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero al objeto COM para el `CFileDialog`. Es su responsabilidad para liberar el puntero this adecuadamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función sólo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] con un objeto que tiene `bVistaStyle` establecido en `true`. Esta función devolverá `NULL` si la `CFileDialog` no es un **guardar** cuadro de diálogo o si `bVistaStyle` está establecido en `false`. En este último caso, la función sólo devuelve `NULL` en modo de lanzamiento - en modo de depuración producirá una aserción.  
  
 Para obtener más información acerca de la `IFileSaveDialog` , vea [IFileSaveDialog](http://msdn.microsoft.com/library/windows/desktop/bb775688).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo recupera el objeto COM interno. Para ejecutar este ejemplo de código, debe compilarlo en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!code-cpp[NVC_MFC_CFileDialog&3;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_6.cpp)]  
  
##  <a name="a-namegetnextpathnamea--cfiledialoggetnextpathname"></a><a name="getnextpathname"></a>CFileDialog::GetNextPathName  
 Llame a esta función para recuperar el siguiente nombre de archivo del grupo seleccionado en el cuadro de diálogo.  
  
```  
CString GetNextPathName(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Una referencia a un **posición** valor devuelto por un método `GetNextPathName` o `GetStartPosition` llamada de función. **NULL** si se ha alcanzado el final de la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Ruta de acceso completa del archivo.  
  
### <a name="remarks"></a>Comentarios  
 La ruta de acceso del nombre de archivo incluye el título del archivo además de la ruta de acceso de todo el directorio. Por ejemplo, `GetNextPathName` devolverá "C:\FILES\TEXT. DAT"para el archivo C:\FILES\TEXT.DAT. Puede usar `GetNextPathName` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetStartPosition`.  
  
 Si la selección se compone de un solo archivo, se devolverá el nombre de archivo.  
  
##  <a name="a-namegetofna--cfiledialoggetofn"></a><a name="getofn"></a>CFileDialog::GetOFN  
 Recupera el asociado **OPENFILENAME** estructura.  
  
```  
const OPENFILENAME& GetOFN() const;  
  
OPENFILENAME& GetOFN();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la segunda versión de esta función para inicializar la apariencia de un **abrir archivo** o **Guardar como** cuadro de diálogo después de que se construye, pero antes de que se muestre con el `DoModal` función miembro. Por ejemplo, puede establecer la **lpstrTitle** miembro de **m_ofn** con el título que desee que el cuadro de diálogo.  
  
##  <a name="a-namegetpathnamea--cfiledialoggetpathname"></a><a name="getpathname"></a>CFileDialog::GetPathName  
 Llame a esta función para recuperar la ruta de acceso completa del archivo especificado en el cuadro de diálogo.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ruta de acceso completa del archivo.  
  
### <a name="remarks"></a>Comentarios  
 La ruta de acceso del nombre de archivo incluye el título del archivo además de la ruta de acceso de todo el directorio. Por ejemplo, `GetPathName` devolverá "C:\FILES\TEXT. DAT"para el archivo C:\FILES\TEXT.DAT.  
  
 Si `m_ofn.Flags` tiene la `OFN_ALLOWMULTISELECT` indicador establecido, esta cadena contiene una secuencia de teminated null cadenas, con la primera cadena que se va a la ruta del directorio del grupo de archivos seleccionado, seguido por los nombres de todos los archivos seleccionados por el usuario. Por este motivo, utilice la [GetStartPosition](#getstartposition) y [GetNextPathName](#getnextpathname) funciones miembro para recuperar el siguiente nombre de archivo en la lista.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFileDialog::DoModal](#domodal).  
  
##  <a name="a-namegetreadonlyprefa--cfiledialoggetreadonlypref"></a><a name="getreadonlypref"></a>CFileDialog::GetReadOnlyPref  
 Llame a esta función para determinar si se ha seleccionado la casilla de verificación de sólo lectura en los cuadros de diálogo Windows abrir archivo y guardar archivo como estándares.  
  
```  
BOOL GetReadOnlyPref() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si está seleccionada la casilla de verificación de sólo lectura en el cuadro de diálogo; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede ocultar la casilla de verificación de sólo lectura estableciendo la `OFN_HIDEREADONLY` de estilo en el `CFileDialog` constructor.  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]estilo `CFileDialog` objetos no admiten esta función. Al intentar utilizar esta función en un [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] estilo `CFileDialog` producirá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).   
  
##  <a name="a-namegetresulta--cfiledialoggetresult"></a><a name="getresult"></a>CFileDialog::GetResult  
 Recupera la opción realizados por el usuario en el cuadro de diálogo.  
  
```  
IShellItem* GetResult() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un IShellItem que representa la elección del usuario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetresultsa--cfiledialoggetresults"></a><a name="getresults"></a>CFileDialog::GetResults  
 Recupera las opciones del usuario en un cuadro de diálogo que permite la selección múltiple.  
  
```  
IShellItemArray* GetResults() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un IShellItemArray a través del cual se pueden tener acceso a los elementos seleccionados en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetselectedcontrolitema--cfiledialoggetselectedcontrolitem"></a><a name="getselectedcontrolitem"></a>CFileDialog::GetSelectedControlItem  
 Recupera un elemento determinado del control contenedor especificado en el cuadro de diálogo.  
  
```  
HRESULT GetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD& dwIDItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento que el usuario seleccionado en el control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetstartpositiona--cfiledialoggetstartposition"></a><a name="getstartposition"></a>CFileDialog::GetStartPosition  
 Llamar a esta función miembro para recuperar la posición de la primera ruta de acceso de archivo en la lista, si `m_ofn.Flags` tiene la `OFN_ALLOWMULTISELECT` marcador establecido.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **posición** valor que puede utilizarse para la iteración; **NULL** si la lista está vacía.  
  
##  <a name="a-namehidecontrola--cfiledialoghidecontrol"></a><a name="hidecontrol"></a>CFileDialog::HideControl  
 Llame a esta función miembro para ocultar el control especificado en un cuadro de diálogo común de estilo explorador abrir o guardar como.  
  
```  
void HideControl(int nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control para ocultar.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo se debe haber creado con el **OFN_EXPLORER** estilo; de lo contrario, la función producirá una aserción.  
  
##  <a name="a-nameispickfoldersmodea--cfiledialogispickfoldersmode"></a><a name="ispickfoldersmode"></a>CFileDialog::IsPickFoldersMode  
 Determina si el cuadro de diálogo actual está en modo selector de carpetas.  
  
```  
BOOL IsPickFoldersMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el cuadro de diálogo está en modo de selector de carpetas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namemofna--cfiledialogmofn"></a><a name="m_ofn"></a>CFileDialog::m_ofn  
 `m_ofn`es una estructura de tipo `OPENFILENAME`. Los datos de esta estructura representan el estado actual de la `CFileDialog`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta estructura para inicializar la apariencia de un **abrir archivo** o **Guardar como** cuadro de diálogo después de crear, pero antes de mostrarlo con el [DoModal](#domodal) método. Por ejemplo, puede establecer la `lpstrTitle` miembro de `m_ofn` con el título que desee que el cuadro de diálogo.  
  
 Con el [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] estilo de [CFileDialog](../../mfc/reference/cfiledialog-class.md), `m_ofn` no se garantiza que siempre coincide con el estado del cuadro de diálogo. Se sincroniza con el cuadro de diálogo en las versiones anteriores de Windows. Consulte [CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog) y [CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog) para obtener más información acerca de cómo sincronizar la `m_ofn` estructura y el `CFileDialog` estado bajo [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]los cuadros de diálogo de archivo de estilo no admiten determinados miembros y los indicadores de la `CFileDialog`. Como resultado, estos no tendrán ningún efecto.  
  
 La siguiente es una lista de los miembros que no son compatibles con [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- `lpstrCustomFilter`  
  
- `lpstrInitialDir`  
  
- `lCustData`  
  
- `lpfnHook`  
  
- `lpTemplateName`  
  
 Las marcas siguientes no se admiten y, por tanto, no tienen ningún efecto cuando se utiliza la [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] estilo de `CFileDialog`:  
  
-   OFN_ENABLEHOOK  
  
-   OFN_ENABLEINCLUDENOTIFY  
  
-   OFN_ENABLETEMPLATE  
  
-   OFN_ENABLETEMPLATEHANDLE  
  
-   OFN_EXPLORER  
  
-   OFN_EXTENSIONDIFFERENT  
  
-   OFN_HIDEREADONLY  
  
-   OFN_LONGNAMES - siempre eficazmente en[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NOLONGNAMES - eficazmente siempre apagado en[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NONETWORKBUTTON - siempre eficazmente en[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_READONLY  
  
-   OFN_SHOWHELP  
  
 Para obtener más información acerca de esta estructura, vea la [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namemakeprominenta--cfiledialogmakeprominent"></a><a name="makeprominent"></a>CFileDialog::MakeProminent  
 Sitios de un control en el cuadro de diálogo para que destaque en comparación con otros controles.  
  
```  
HRESULT MakeProminent(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonbuttonclickeda--cfiledialogonbuttonclicked"></a><a name="onbuttonclicked"></a>CFileDialog::OnButtonClicked  
 Se llama cuando se hace clic en el botón.  
  
```  
virtual void OnButtonClicked(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoncheckbuttontoggleda--cfiledialogoncheckbuttontoggled"></a><a name="oncheckbuttontoggled"></a>CFileDialog::OnCheckButtonToggled  
 Se llama cuando la casilla de verificación está activada o desactivada.  
  
```  
virtual void OnCheckButtonToggled(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador de la casilla de verificación.  
  
 `bChecked`  
 Activado o desactivado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoncontrolactivatinga--cfiledialogoncontrolactivating"></a><a name="oncontrolactivating"></a>CFileDialog::OnControlActivating  
 Se llama cuando se activa el control.  
  
```  
virtual void OnControlActivating(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonfilenamechangea--cfiledialogonfilenamechange"></a><a name="onfilenamechange"></a>CFileDialog::OnFileNameChange  
 Invalide este método si desea controlar el `WM_NOTIFY``CDN_SELCHANGE` mensaje.  
  
```  
virtual void OnFileNameChange();
```  
  
### <a name="remarks"></a>Comentarios  
 El sistema envía el `CDN_SELCHANGE` de mensaje cuando el usuario selecciona un nuevo archivo o carpeta en la lista de archivos de la **abiertos** o **Guardar como** cuadro de diálogo. Invalide este método si desea realizar acciones en respuesta a este mensaje.  
  
 El sistema envía este mensaje sólo si el cuadro de diálogo se creó con la marca OFN_EXPLORER activada. Para obtener más información acerca de la notificación, consulte [CDN_SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646865). Para obtener información acerca de la marca OFN_EXPLORER, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura y [abrir y guardar como cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="a-nameonfilenameoka--cfiledialogonfilenameok"></a><a name="onfilenameok"></a>CFileDialog::OnFileNameOK  
 Reemplace esta función sólo si desea proporcionar validación personalizada de los nombres de archivo que se introducen en un cuadro de diálogo de archivos común.  
  
```  
virtual BOOL OnFileNameOK();
```  
  
### <a name="return-value"></a>Valor devuelto  
 1 si el nombre de archivo no es válido; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función permite rechazar un nombre de archivo por alguna razón específica de la aplicación. Normalmente, no es necesario usar esta función porque el marco de trabajo proporciona validación predeterminada de nombres de archivo y muestra un cuadro de mensaje si se introduce un nombre de archivo no válido.  
  
 Si se devuelve 1, el cuadro de diálogo permanecerá mostrado para el usuario que escriba otro nombre de archivo. El procedimiento de cuadro de diálogo cierra el cuadro de diálogo si el valor devuelto es 0. Otro distinto de cero, se devuelve valores están reservados actualmente y no deben usarse.  
  
##  <a name="a-nameonfolderchangea--cfiledialogonfolderchange"></a><a name="onfolderchange"></a>CFileDialog::OnFolderChange  
 Reemplazar esta función para controlar la **WM_NOTIFYCDN_FOLDERCHANGE** mensaje.  
  
```  
virtual void OnFolderChange();
```  
  
### <a name="remarks"></a>Comentarios  
 El mensaje de notificación se envía cuando se abre una nueva carpeta en el cuadro de diálogo Abrir o guardar como.  
  
 Se envía la notificación solo si el cuadro de diálogo se creó con el estilo OFN_EXPLORER. Para obtener más información acerca de la notificación, consulte [CDN_FOLDERCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646859). Para obtener información sobre el estilo OFN_EXPLORER, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura y [abrir y guardar como cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="a-nameoninitdonea--cfiledialogoninitdone"></a><a name="oninitdone"></a>CFileDialog::OnInitDone  
 Reemplazar esta función para controlar la `WM_NOTIFY``CDN_INITDONE` mensaje.  
  
```  
virtual void OnInitDone();
```  
  
### <a name="remarks"></a>Comentarios  
 El sistema envía este mensaje de notificación cuando el sistema haya terminado de organizar los controles en el **abiertos** o **Guardar como** cuadro de diálogo para dejar espacio a los controles del cuadro de diálogo secundario.  
  
 El sistema envía esto sólo si el cuadro de diálogo se creó con el estilo OFN_EXPLORER. Para obtener más información acerca de la notificación, consulte [CDN_INITDONE](http://msdn.microsoft.com/library/windows/desktop/ms646863). Para obtener información sobre el estilo OFN_EXPLORER, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura y [abrir y guardar como cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]los cuadros de diálogo de archivo de estilo no admiten esta función. Al intentar utilizar esta función en un [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] iniciará el cuadro de diálogo de archivo de estilo [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md). 
  
##  <a name="a-nameonitemselecteda--cfiledialogonitemselected"></a><a name="onitemselected"></a>CFileDialog::OnItemSelected  
 Se llama cuando se selecciona el elemento contenedor.  
  
```  
virtual void OnItemSelected(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonlbselchangednotifya--cfiledialogonlbselchangednotify"></a><a name="onlbselchangednotify"></a>CFileDialog::OnLBSelChangedNotify  
 Esta función se invoca siempre que la selección actual en un cuadro de lista se va a cambiar.  
  
```  
virtual void OnLBSelChangedNotify(
    UINT nIDBox,  
    UINT iCurSel,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDBox*  
 El identificador del cuadro de lista o cuadro combinado en el que se produjo la selección.  
  
 `iCurSel`  
 El índice de la selección actual.  
  
 `nCode`  
 El código de notificación del control. Este parámetro debe tener uno de los siguientes valores:  
  
- **CD_LBSELCHANGE** especifica `iCurSel` es el elemento seleccionado en un cuadro de lista de selección única.  
  
- **CD_LBSELSUB** especifica que `iCurSel` ya no está seleccionado en un cuadro de lista de selección múltiple.  
  
- **CD_LBSELADD** especifica que `iCurSel` está seleccionado en un cuadro de lista de selección múltiple.  
  
- **CD_LBSELNOITEMS** especifica que no hay nada seleccionado existe en un cuadro de lista de selección múltiple.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para proporcionar un control personalizado de cambios de selección en el cuadro de lista. Por ejemplo, puede utilizar esta función para mostrar los derechos de acceso o la fecha de última modificación de cada archivo que el usuario selecciona.  
  
##  <a name="a-nameonshareviolationa--cfiledialogonshareviolation"></a><a name="onshareviolation"></a>CFileDialog::OnShareViolation  
 Reemplazar esta función para proporcionar un control personalizado de infracciones de recurso compartido.  
  
```  
virtual UINT OnShareViolation(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 La ruta de acceso del archivo en el que se produjo la infracción de recurso compartido.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores:  
  
- **OFN_SHAREFALLTHROUGH** se devuelve el nombre de archivo en el cuadro de diálogo.  
  
- **OFN_SHARENOWARN** no hay que realizar ninguna acción adicional.  
  
- **OFN_SHAREWARN** el usuario recibe el mensaje de advertencia estándar para este error.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, no es necesario usar esta función porque el marco de trabajo proporciona una comprobación de infracciones de recurso compartido predeterminado y muestra un cuadro de mensaje si se produce una infracción de recurso compartido.  
  
 Si desea deshabilitar la comprobación de infracción de recurso compartido, utilice el operador OR bit a bit para combinar la marca **OFN_SHAREAWARE** con `m_ofn.Flags`.  
  
##  <a name="a-nameontypechangea--cfiledialogontypechange"></a><a name="ontypechange"></a>CFileDialog::OnTypeChange  
 Reemplazar esta función para controlar la **WM_NOTIFYCDN_TYPECHANGE** mensaje.  
  
```  
virtual void OnTypeChange();
```  
  
### <a name="remarks"></a>Comentarios  
 El mensaje de notificación se envía cuando el usuario selecciona un nuevo tipo de archivo de la lista de tipos de archivo en el cuadro Abrir o el cuadro de diálogo Guardar como.  
  
 Se envía la notificación solo si el cuadro de diálogo se creó con el estilo OFN_EXPLORER. Para obtener más información acerca de la notificación, consulte [CDN_TYPECHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646868). Para obtener información sobre el estilo OFN_EXPLORER, consulte el [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) estructura y [abrir y guardar como cuadros de diálogo](http://msdn.microsoft.com/library/windows/desktop/ms646960).  
  
##  <a name="a-nameremovecontrolitema--cfiledialogremovecontrolitem"></a><a name="removecontrolitem"></a>CFileDialog::RemoveControlItem  
 Quita un elemento de un control contenedor en el cuadro de diálogo.  
  
```  
HRESULT RemoveControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor para quitar el elemento de.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcheckbuttonstatea--cfiledialogsetcheckbuttonstate"></a><a name="setcheckbuttonstate"></a>CFileDialog::SetCheckButtonState  
 Establece el estado actual de un botón de comprobación (casilla de verificación) en el cuadro de diálogo.  
  
```  
HRESULT SetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador de la casilla de verificación.  
  
 `bChecked`  
 El estado de la casilla de verificación. `TRUE`indica comprobado; `FALSE` indica si está desactivada.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcontrolitemstatea--cfiledialogsetcontrolitemstate"></a><a name="setcontrolitemstate"></a>CFileDialog::SetControlItemState  
 Establece el estado actual de un elemento en un control contenedor que se encuentra en el cuadro de diálogo.  
  
```  
HRESULT SetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
 `dwState`  
 Uno o más valores de la enumeración CDCONTROLSTATE que indiquen el nuevo estado del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcontrolitemtexta--cfiledialogsetcontrolitemtext"></a><a name="setcontrolitemtext"></a>CFileDialog::SetControlItemText  
 Establece el texto de un elemento del control. Por ejemplo, el texto que acompaña a un elemento en un menú o un botón de radio.  
  
```  
HRESULT SetControlItemText(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento.  
  
 `strLabel`  
 Texto del elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcontrollabela--cfiledialogsetcontrollabel"></a><a name="setcontrollabel"></a>CFileDialog::SetControlLabel  
 Establece el texto asociado a un control, como el texto del botón o una etiqueta de cuadro de edición.  
  
```  
HRESULT SetControlLabel(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control.  
  
 `strLabel`  
 El nombre del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcontrolstatea--cfiledialogsetcontrolstate"></a><a name="setcontrolstate"></a>CFileDialog::SetControlState  
 Establece la visibilidad actual y habilita los Estados de un control determinado.  
  
```  
HRESULT SetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control.  
  
 `dwState`  
 Uno o más valores de la enumeración CDCONTROLSTATE que indican el estado actual del control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetcontroltexta--cfiledialogsetcontroltext"></a><a name="setcontroltext"></a>CFileDialog::SetControlText  
 Llamar a este método para establecer el texto para el control especificado en un tipo de explorador **abiertos** o **Guardar como** cuadro de diálogo.  
  
```  
void SetControlText(
    int nID,  
    LPCSTR lpsz);

 
void SetControlText(
    int nID,  
    const wchar_t *lpsz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de control para el que se va a establecer el texto.  
  
 [in] `lpsz`  
 Puntero a la cadena que contiene el texto que se va a establecer para el control.  
  
### <a name="remarks"></a>Comentarios  
 Ambas versiones de esta función son válidos para las aplicaciones que utilizan Unicode. Sin embargo, sólo la versión con el tipo LPCSTR es válida para las aplicaciones que utilizan [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)].  
  
 Para utilizar este método, debe crear el cuadro de diálogo con el estilo OFN_EXPLORER. De lo contrario, se producirá un error de la función con una aserción.  
  
##  <a name="a-namesetdefexta--cfiledialogsetdefext"></a><a name="setdefext"></a>CFileDialog::SetDefExt  
 Llame a esta función para establecer la extensión de nombre de archivo predeterminado para un cuadro de diálogo común de estilo explorador abrir o guardar como.  
  
```  
void SetDefExt(LPCSTR lpsz);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 Puntero a una cadena que contiene la extensión predeterminada que se utilizará para el objeto de cuadro de diálogo. Esta cadena no debe contener un punto (.).  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo se debe haber creado con el **OFN_EXPLORER** estilo; de lo contrario, la función producirá una aserción.  
  
##  <a name="a-nameseteditboxtexta--cfiledialogseteditboxtext"></a><a name="seteditboxtext"></a>CFileDialog::SetEditBoxText  
 Establece el texto actual en un control de cuadro de edición.  
  
```  
HRESULT SetEditBoxText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del cuadro de edición.  
  
 `strText`  
 Valor de texto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpropertiesa--cfiledialogsetproperties"></a><a name="setproperties"></a>CFileDialog::SetProperties  
 Proporciona un almacén de propiedades que define los valores predeterminados que se van a usar para el elemento que se está guardando.  
  
```  
BOOL SetProperties(LPCWSTR lpszPropList);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPropList`  
 Lista de propiedades predefinidas separadas por ";". Para obtener una lista de los indicadores, consulte la `Flags` sección de [OPENFILENAME](http://msdn.microsoft.com/en-us/8cecfd45-f7c1-4f8d-81a0-4e7fecc3b104).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetselectedcontrolitema--cfiledialogsetselectedcontrolitem"></a><a name="setselectedcontrolitem"></a>CFileDialog::SetSelectedControlItem  
 Establece el estado seleccionado de un elemento determinado en un grupo de botones de opción o un cuadro combinado que se encuentra en el cuadro de diálogo.  
  
```  
HRESULT SetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del control contenedor.  
  
 `dwIDItem`  
 Identificador del elemento que el usuario seleccionado en el control.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettemplatea--cfiledialogsettemplate"></a><a name="settemplate"></a>CFileDialog::SetTemplate  
 Establece la plantilla de cuadro de diálogo para la [CFileDialog](../../mfc/reference/cfiledialog-class.md) objeto.  
  
```  
void SetTemplate(
    UINT nWin3ID,  
    UINT nWin4ID);

 
void SetTemplate(
    LPCTSTR lpWin3ID,  
    LPCTSTR lpWin4ID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nWin3ID`  
 Contiene el número de Id. de recurso de plantilla para el usuario que no sea explorador `CFileDialog` objeto. Esta plantilla se usa sólo en Windows NT 3.51 o cuando el estilo OFN_EXPLORER no está presente.  
  
 [in] `nWin4ID`  
 Contiene el número de Id. de recurso de plantilla para el Explorador de `CFileDialog` objeto. Esta plantilla se usa solo en [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] y versiones posteriores, Windows 95 y versiones posteriores, o cuando el estilo OFN_EXPLORER está presente.  
  
 [in] `lpWin3ID`  
 Contiene el nombre del recurso de plantilla para el usuario que no sea explorador `CFileDialog` objeto. Esta plantilla se usa sólo en Windows NT 3.51 o cuando el estilo OFN_EXPLORER no está presente.  
  
 [in] `lpWin4ID`  
 Contiene el nombre del recurso de plantilla del explorador `CFileDialog` objeto. Esta plantilla se usa solo en [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] y versiones posteriores, Windows 95 y versiones posteriores, o cuando el estilo OFN_EXPLORER está presente.  
  
### <a name="remarks"></a>Comentarios  
 El sistema usará sólo una de las plantillas especificadas. El sistema determina qué plantilla utilizar basándose en la presencia del estilo OFN_EXPLORER y el sistema operativo que se ejecuta la aplicación. Al especificar un explorador no y la plantilla de estilo de explorador, es fácil al soporte técnico de Windows NT 3.51, [!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)] y versiones posteriores y Windows 95 y versiones posteriores.  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]cuadros de diálogo de archivo de estilo no admiten esta función. Al intentar utilizar esta función en un [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] iniciará el cuadro de diálogo de archivo de estilo [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md). Una alternativa es utilizar un cuadro de diálogo personalizado. Para obtener más información acerca de cómo utilizar un personalizado `CFileDialog`, consulte [IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912).  
  
##  <a name="a-namestartvisualgroupa--cfiledialogstartvisualgroup"></a><a name="startvisualgroup"></a>CFileDialog::StartVisualGroup  
 Declara un grupo visual en el cuadro de diálogo. Las llamadas subsiguientes a cualquier método "add" agregan esos elementos a este grupo.  
  
```  
HRESULT StartVisualGroup(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwIDCtl`  
 El identificador del grupo visual.  
  
 `strLabel`  
 El nombre del grupo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameupdateofnfromshelldialoga--cfiledialogupdateofnfromshelldialog"></a><a name="updateofnfromshelldialog"></a>CFileDialog::UpdateOFNFromShellDialog  
 Las actualizaciones de la `m_ofn` estructura de datos de la [CFileDialog](../../mfc/reference/cfiledialog-class.md) basándose en el estado actual del objeto interno.  
  
```  
void UpdateOFNFromShellDialog();
```  
  
### <a name="remarks"></a>Comentarios  
 En las versiones de Windows anteriores a [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], el miembro [OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx) estructura de datos se sincroniza continuamente con el estado de la `CFileDialog`. Los cambios realizados en el [m_ofn](#m_ofn) variable miembro se ve directamente afectado el estado del cuadro de diálogo. Además, cualquier cambio en el estado del cuadro de diálogo actualiza inmediatamente en la variable de miembro m_ofn.  
  
 En [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], el `m_ofn` estructura de datos no se actualiza automáticamente. Para garantizar la exactitud de los datos de la `m_ofn` variable miembro, se debe llamar a la `UpdateOFNFromShellDialog` función antes de acceder a los datos. Windows llama a esta función automáticamente durante el procesamiento de [IFileDialog::OnFileOK](http://msdn.microsoft.com/library/windows/desktop/bb775879).  
  
 Para obtener más información acerca de cómo utilizar el `CFileDialog` en la clase [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], consulte [clase CFileDialog](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo actualiza el `CFileDialog` antes de mostrarlo. Antes de actualizar el `m_ofn` variable miembro, necesitamos sincronizarlo con el estado actual del cuadro de diálogo.  
  
 [!code-cpp[1 NVC_MFC_CFileDialog](../../mfc/reference/codesnippet/cpp/cfiledialog-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


