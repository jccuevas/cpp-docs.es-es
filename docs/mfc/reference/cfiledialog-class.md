---
title: "CFileDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileDialog class"
  - "common file dialog boxes"
  - "cuadros de diálogo, common"
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula el cuadro de diálogo común que se usa para el archivo abierto u operaciones de almacenamiento de archivo.  
  
## Sintaxis  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)|Crea un objeto `CFileDialog`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CFileDialog::AddCheckButton](../Topic/CFileDialog::AddCheckButton.md)|Agrega un botón de comprobación al diálogo.|  
|[CFileDialog::AddComboBox](../Topic/CFileDialog::AddComboBox.md)|Agrega un cuadro combinado el diálogo.|  
|[CFileDialog::AddControlItem](../Topic/CFileDialog::AddControlItem.md)|Agrega un elemento a un control contenedor en el diálogo.|  
|[CFileDialog::AddEditBox](../Topic/CFileDialog::AddEditBox.md)|Agrega un cuadro de edición al diálogo.|  
|[CFileDialog::AddMenu](../Topic/CFileDialog::AddMenu.md)|Agrega un menú al diálogo.|  
|[CFileDialog::AddPlace](../Topic/CFileDialog::AddPlace.md)|Sobrecargado.  Agrega una carpeta a la lista de lugares disponibles para que el usuario abra o guarde elementos.|  
|[CFileDialog::AddPushButton](../Topic/CFileDialog::AddPushButton.md)|Agrega un botón al diálogo.|  
|[CFileDialog::AddRadioButtonList](../Topic/CFileDialog::AddRadioButtonList.md)|Agrega un grupo de botones de radio \(también conocido como botón de radio\) al diálogo.|  
|[CFileDialog::AddSeparator](../Topic/CFileDialog::AddSeparator.md)|Agrega un separador el diálogo.|  
|[CFileDialog::AddText](../Topic/CFileDialog::AddText.md)|Agrega el contenido de texto al diálogo.|  
|[CFileDialog::ApplyOFNToShellDialog](../Topic/CFileDialog::ApplyOFNToShellDialog.md)|Actualiza el estado `CFileDialog` para hacer coincidir los parámetros y los marcadores almacenados en la variable miembro `m_ofn` .|  
|[CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md)|Muestra el cuadro de diálogo y permite al usuario crear una selección.|  
|[CFileDialog::EnableOpenDropDown](../Topic/CFileDialog::EnableOpenDropDown.md)|Habilita una lista desplegable del botón **Abrir** o **Guardar** en el diálogo.|  
|[CFileDialog::EndVisualGroup](../Topic/CFileDialog::EndVisualGroup.md)|Detiene la adición de elementos a un grupo visual en el diálogo.|  
|[CFileDialog::GetCheckButtonState](../Topic/CFileDialog::GetCheckButtonState.md)|Obtiene el estado actual de un botón de comprobación \(casilla\) en el cuadro de diálogo.|  
|[CFileDialog::GetControlItemState](../Topic/CFileDialog::GetControlItemState.md)|Obtiene el estado actual de un elemento en un control contenedor se encuentra en el diálogo.|  
|[CFileDialog::GetControlState](../Topic/CFileDialog::GetControlState.md)|Obtiene la visibilidad actual y estados habilitadas de un control determinado.|  
|[CFileDialog::GetEditBoxText](../Topic/CFileDialog::GetEditBoxText.md)|Obtiene el texto actual en un control de cuadro de edición.|  
|[CFileDialog::GetFileExt](../Topic/CFileDialog::GetFileExt.md)|Devuelve la extensión del archivo seleccionado.|  
|[CFileDialog::GetFileName](../Topic/CFileDialog::GetFileName.md)|Devuelve el nombre del archivo seleccionado.|  
|[CFileDialog::GetFileTitle](../Topic/CFileDialog::GetFileTitle.md)|Devuelve el título del archivo seleccionado.|  
|[CFileDialog::GetFolderPath](../Topic/CFileDialog::GetFolderPath.md)|Recupera la ruta de acceso de la carpeta o el directorio abierta para un Explorador\- estilo **Abrir** o el cuadro de diálogo común **Guardar como** .|  
|[CFileDialog::GetIFileDialogCustomize](../Topic/CFileDialog::GetIFileDialogCustomize.md)|Recupera el objeto COM interno para un objeto personalizado `CFileDialog` .|  
|[CFileDialog::GetIFileOpenDialog](../Topic/CFileDialog::GetIFileOpenDialog.md)|Recupera el objeto COM interno para `CFileDialog` que se utiliza como cuadro de diálogo archivos **Abrir** .|  
|[CFileDialog::GetIFileSaveDialog](../Topic/CFileDialog::GetIFileSaveDialog.md)|Recupera el objeto COM interno para `CFileDialog` que se utiliza como cuadro de diálogo archivos **Guardar** .|  
|[CFileDialog::GetNextPathName](../Topic/CFileDialog::GetNextPathName.md)|Devuelve la ruta de acceso completa del archivo seleccionado siguiente.|  
|[CFileDialog::GetOFN](../Topic/CFileDialog::GetOFN.md)|Recupera la estructura `OPENFILENAME` del objeto `CFileDialog` .|  
|[CFileDialog::GetPathName](../Topic/CFileDialog::GetPathName.md)|Devuelve la ruta de acceso completa del archivo seleccionado.|  
|[CFileDialog::GetReadOnlyPref](../Topic/CFileDialog::GetReadOnlyPref.md)|Devuelve el estado de sólo lectura del archivo seleccionado.|  
|[CFileDialog::GetResult](../Topic/CFileDialog::GetResult.md)|Obtiene la decisión que el usuario tomado en el diálogo.|  
|[CFileDialog::GetResults](../Topic/CFileDialog::GetResults.md)|Obtiene las opciones de usuario en un cuadro de diálogo que permite la selección múltiple.|  
|[CFileDialog::GetSelectedControlItem](../Topic/CFileDialog::GetSelectedControlItem.md)|Obtiene un elemento de los controles contenedor especificados en el cuadro de diálogo.|  
|[CFileDialog::GetStartPosition](../Topic/CFileDialog::GetStartPosition.md)|Devuelve la posición del primer elemento de la lista de nombres de archivo.|  
|[CFileDialog::HideControl](../Topic/CFileDialog::HideControl.md)|Oculta el control especificado en un Explorador\-estilo **Abrir** o el cuadro de diálogo común **Guardar como** .|  
|[CFileDialog::IsPickFoldersMode](../Topic/CFileDialog::IsPickFoldersMode.md)|Determina si el diálogo actual en modo de selector de carpetas.|  
|[CFileDialog::MakeProminent](../Topic/CFileDialog::MakeProminent.md)|Coloque un control en el diálogo de modo que se coloque out comparado con otros controles agregados.|  
|[CFileDialog::RemoveControlItem](../Topic/CFileDialog::RemoveControlItem.md)|Quita un elemento de un control contenedor en el cuadro de diálogo.|  
|[CFileDialog::SetCheckButtonState](../Topic/CFileDialog::SetCheckButtonState.md)|Establece el estado actual de un botón de comprobación \(casilla\) en el cuadro de diálogo.|  
|[CFileDialog::SetControlItemState](../Topic/CFileDialog::SetControlItemState.md)|Establece el estado actual de un elemento en un control contenedor se encuentra en el diálogo.|  
|[CFileDialog::SetControlItemText](../Topic/CFileDialog::SetControlItemText.md)|Establece el texto de un elemento del control.  Por ejemplo, el texto que acompaña a un botón de opción o un elemento de un menú.|  
|[CFileDialog::SetControlLabel](../Topic/CFileDialog::SetControlLabel.md)|Establece el texto asociado a un control, como texto del botón o una etiqueta del cuadro de edición.|  
|[CFileDialog::SetControlState](../Topic/CFileDialog::SetControlState.md)|Establece la visibilidad actual y estados habilitadas de un control determinado.|  
|[CFileDialog::SetControlText](../Topic/CFileDialog::SetControlText.md)|Establece el texto del control especificado en un Explorador\- estilo **Abrir** o el cuadro de diálogo común **Guardar como** .|  
|[CFileDialog::SetDefExt](../Topic/CFileDialog::SetDefExt.md)|Establece la extensión de nombre de archivo predeterminada para un Explorador\-estilo **Abrir** o el cuadro de diálogo común **Guardar como** .|  
|[CFileDialog::SetEditBoxText](../Topic/CFileDialog::SetEditBoxText.md)|Establece el texto actual en un control de cuadro de edición.|  
|[CFileDialog::SetProperties](../Topic/CFileDialog::SetProperties.md)|Proporciona una propiedad almacenada que define los valores predeterminados que se utilizará para el elemento que se está guardando.|  
|[CFileDialog::SetSelectedControlItem](../Topic/CFileDialog::SetSelectedControlItem.md)|Establece el estado seleccionado de un elemento determinado en un grupo de botones de radio o un cuadro combinado encontró en el diálogo.|  
|[CFileDialog::SetTemplate](../Topic/CFileDialog::SetTemplate.md)|Establece la plantilla en el cuadro de diálogo para el objeto `CFileDialog` .|  
|[CFileDialog::StartVisualGroup](../Topic/CFileDialog::StartVisualGroup.md)|Declara un grupo visual en el diálogo.  Las llamadas subsiguientes a cualquier “add” método agregan los elementos a este grupo.|  
|[CFileDialog::UpdateOFNFromShellDialog](../Topic/CFileDialog::UpdateOFNFromShellDialog.md)|Actualiza los datos almacenados en la variable miembro `m_ofn` para que coincida con el estado actual del cuadro de diálogo de archivos.|  
  
### Métodos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CFileDialog::OnButtonClicked](../Topic/CFileDialog::OnButtonClicked.md)|Llamado cuando se hace clic en el botón.|  
|[CFileDialog::OnCheckButtonToggled](../Topic/CFileDialog::OnCheckButtonToggled.md)|Llamado cuando la casilla está activada o desactivada.|  
|[CFileDialog::OnControlActivating](../Topic/CFileDialog::OnControlActivating.md)|Se llama cuando el control se está activo.|  
|[CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md)|Controla el mensaje `WM_NOTIFY CDN_SELCHANGE` .|  
|[CFileDialog::OnFileNameOK](../Topic/CFileDialog::OnFileNameOK.md)|Valida el nombre de archivo especificado en el cuadro de diálogo.|  
|[CFileDialog::OnFolderChange](../Topic/CFileDialog::OnFolderChange.md)|Controla el mensaje `WM_NOTIFY CDN_FOLDERCHANGE` .|  
|[CFileDialog::OnInitDone](../Topic/CFileDialog::OnInitDone.md)|Controla el mensaje `WM_NOTIFY CDN_INITDONE` .|  
|[CFileDialog::OnItemSelected](../Topic/CFileDialog::OnItemSelected.md)|Se invoca cuando se seleccione el elemento del contenedor.|  
|[CFileDialog::OnLBSelChangedNotify](../Topic/CFileDialog::OnLBSelChangedNotify.md)|Permite realizar acciones personalizadas cuando cambia la selección de archivos.|  
|[CFileDialog::OnShareViolation](../Topic/CFileDialog::OnShareViolation.md)|Controla las infracciones de recurso compartido.|  
|[CFileDialog::OnTypeChange](../Topic/CFileDialog::OnTypeChange.md)|Controla el mensaje `WM_NOTIFY CDN_TYPECHANGE` .|  
  
### Miembros de datos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md)|La estructura de Windows `OPENFILENAME` .  Proporciona acceso a los parámetros básicos del cuadro de diálogo de archivos.|  
  
## Comentarios  
 Los cuadros de diálogo de archivos comunes permiten implementar los cuadros de diálogo de selección de archivos, por ejemplo, **Abrir archivo** y **Guardar como**, de manera compatible con los estándares de Windows.  
  
 Puede utilizar [CFileDialog](../../mfc/reference/cfiledialog-class.md) como es mediante el constructor proporcionado, o puede derivar dispone de la del cuadro de diálogo `CFileDialog` y escribir un constructor para satisfacer las necesidades.  En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo estándar de MFC dado que se derivan [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md).  `CFileDialog` se basa en el archivo de COMMDLG.DLL que incluye Windows.  
  
 La apariencia y la funcionalidad `CFileDialog` con [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] difieren de las versiones anteriores de Windows.  El valor predeterminado `CFileDialog` utiliza automáticamente el nuevo estilo [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] sin cambios de código si se compila un programa y ejecución en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  Utilice el parámetro `bVistaStyle` en el constructor para invalidar manualmente esta actualización automática.  La excepción a la actualización automática es cuadros de diálogo personalizados.  No se convierten al nuevo estilo.  Para obtener más información sobre el constructor, vea [CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md).  
  
> [!NOTE]
>  El control ID System diferencia en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] de versiones anteriores de Windows cuando se utiliza `CFileDialog`.  Debe actualizar todas las referencias a los controles `CFileDialog` en código antes de poder puerto el proyecto de una versión anterior de Windows.  
  
 Algunos métodos `CFileDialog` no se admiten en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  Compruebe el tema individual de método para la información sobre si el método está admitido.  Además, las funciones heredadas siguientes no se admiten en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
-   [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)  
  
-   [CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)  
  
 Los mensajes de windows para la clase `CFileDialog` varían en función del sistema operativo utiliza.  Por ejemplo, Windows XP no admite [CDialog::OnCancel](../Topic/CDialog::OnCancel.md) y [CDialog::OnOK](../Topic/CDialog::OnOK.md) para la clase `CFileDialog` .  Sin embargo, [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] los admite.  Para obtener más información sobre los distintos mensajes que se generan y el orden en que se reciben, vea [Ejemplo de CFileDialog: Orden del evento de registro](../../top/visual-cpp-samples.md).  
  
 Para utilizar un objeto `CFileDialog` , primero cree el objeto mediante el constructor `CFileDialog` .  Una vez construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la estructura [CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md) para inicializar los valores o estados de los controles de cuadro de diálogo.  La estructura `m_ofn` es `OPENFILENAME`escrito.  Para obtener más información, vea la estructura [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Después de inicializar los controles de cuadro de diálogo, llame al método [CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md) para mostrar el cuadro de diálogo para que el usuario puede escribir la ruta de acceso y nombre de archivo.  `DoModal` devuelve si el usuario hizo clic en ACEPTAR \(IDOK\) o el botón cancelar \(IDCANCEL\).  Si `DoModal` devuelve IDOK, puede utilizar una de las funciones públicas del miembro `CFileDialog` para recuperar la información introducida por el usuario.  
  
> [!NOTE]
>  En [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)], las llamadas a [IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980) producen un error.  La segunda llamada a `SetFileTypes` para cualquier instancia `CFileDialog` devolverá `E_UNEXPECTED` en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  Alguna llamada de funciones del método `CFileDialog``SetFileTypes`.  Por ejemplo, dos llamadas a `CFileDialog::DoModal` para la misma instancia `CFileDialog` generan [ASSERT](../Topic/ASSERT%20\(MFC\).md).  
  
 `CFileDialog` incluye varios miembros protegidos que permiten hacer administrar personalizado de infracciones de recurso compartido, la validación del nombre de archivo, y la notificación del cuadro de lista.  Estos miembros protegidos son funciones de devolución de llamada que la mayoría de las aplicaciones no tienen que usar porque el control predeterminado se realiza automáticamente.  Las entradas de Mensaje\- mapa para estas funciones no se requieren porque son funciones virtuales estándar.  
  
 Puede utilizar la función de Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  
  
 La destrucción de objetos `CFileDialog` se controla automáticamente.  No tiene que llamar a [CDialog::EndDialog](../Topic/CDialog::EndDialog.md).  
  
 Para permitir al usuario seleccionar varios archivos, especifique el marcador `OFN_ALLOWMULTISELECT` antes de llamar a `DoModal`.  Debe proporcionar dispone del búfer de nombre de archivo para alojar la lista devuelta de nombres de varios archivos.  Haga esto reemplazando `m_ofn.lpstrFile` con un puntero a un búfer que ha asignado, después de crear `CFileDialog`, pero antes de que se llama a `DoModal`.  
  
 Además, debe establecer `m_ofn.nMaxFile` mediante el número de caracteres del búfer indicada por `m_ofn.lpstrFile`.  Si establece el número máximo de archivos que se seleccionen en `n`, el tamaño de búfer necesario es `n * (_MAX_PATH + 1) + 1`.  El primer elemento devuelto en el búfer es la ruta de la carpeta donde los archivos seleccionados.  Para [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]\- los cuadros de diálogo del estilo, el directorio y cadenas de nombre de archivo son terminada en null, con un carácter null adicional después del nombre de archivo pasado.  Este formato permite a cuadros de diálogo de Explorador\- estilo para devolver los nombres de archivo largos que incluyen espacios.  Para los cuadros de diálogo antiguo, el directorio y cadenas de nombre de archivo están separados por espacios y la función utiliza los nombres de archivo cortos para los nombres de archivo con espacios.  
  
 El ejemplo siguiente se muestra cómo utilizar un búfer para recuperar y enumerar nombres de varios archivos.  
  
 [!code-cpp[NVC_MFCFiles#23](../../mfc/codesnippet/CPP/cfiledialog-class_1.cpp)]  
  
 Para cambiar el tamaño de búfer en respuesta al usuario que selecciona nombres de varios archivos, debe derivar una nueva clase `CFileDialog` y reemplazar el método [CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md) .  
  
 Si deriva una nueva clase `CFileDialog`, puede utilizar un mapa de mensajes para administrar cualquier mensaje.  Para extender el control de mensajes predeterminada, derive una clase `CFileDialog`, agregar un mensaje asignado a la nueva clase, y proporcionar funciones de miembro para los nuevos mensajes.  No tiene que proporcionar una función de enlace para personalizar el cuadro de diálogo.  
  
 Para personalizar el cuadro de diálogo, derive una clase `CFileDialog`, proporcionar una plantilla personalizada del cuadro de diálogo, y agregar un mapa de mensajes para procesar mensajes de notificación de controles extendidos.  Pase los mensajes sin procesar a la clase base.  No tiene que personalizar la función de enlace.  
  
 Cuando se utiliza el estilo [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]`CFileDialog`, no puede utilizar mapas de mensajes y plantillas del cuadro de diálogo.  En su lugar, debería utilizar las interfaces COM para la funcionalidad similar.  
  
 Para obtener más información acerca de cómo se usa `CFileDialog`, vea [Clases de cuadros de diálogo comunes](../../mfc/common-dialog-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## Requisitos  
 **Encabezado:** afxdlgs.h  
  
## Vea también  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)