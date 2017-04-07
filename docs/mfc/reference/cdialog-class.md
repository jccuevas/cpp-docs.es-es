---
title: CDialog (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes, creating
- MFC dialog boxes, base class
- modeless dialog boxes, creating
- modeless dialog boxes, displaying
- CDialog class
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: d06d072dd62eed102c3073cd1cd7a0c112e674bb
ms.lasthandoff: 04/01/2017

---
# <a name="cdialog-class"></a>CDialog (clase)
La clase base utilizada para mostrar cuadros de diálogo en la pantalla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|Construye un objeto `CDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDialog::Create](#create)|Inicializa el `CDialog` objeto. Crea un cuadro de diálogo no modal y lo adjunta a la `CDialog` objeto.|  
|[CDialog::CreateIndirect](#createindirect)|Crea un cuadro de diálogo no modal de una plantilla de cuadro de diálogo en memoria (no basada en recursos).|  
|[CDialog::DoModal](#domodal)|Llama a un cuadro de diálogo modal y devuelve cuando haya finalizado.|  
|[CDialog::EndDialog](#enddialog)|Cierra el cuadro de diálogo modal.|  
|[CDialog::GetDefID](#getdefid)|Obtiene el identificador del control de botón de comando predeterminado de un cuadro de diálogo.|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Mueve el foco a un control de cuadro de diálogo especificado en el cuadro de diálogo.|  
|[CDialog:: InitModalIndirect](#initmodalindirect)|Crea un cuadro de diálogo modal de una plantilla de cuadro de diálogo en memoria (no basada en recursos). Los parámetros se almacenan hasta que la función `DoModal` se llama.|  
|[CDialog::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Mueve el foco al siguiente control de cuadro de diálogo en el cuadro de diálogo.|  
|[CDialog:: OnInitDialog](#oninitdialog)|Reemplace este valor para aumentar la inicialización del cuadro de diálogo.|  
|[CDialog::OnSetFont](#onsetfont)|Reemplace este valor para especificar la fuente que un control de cuadro de diálogo que se va a usar cuando dibuja el texto.|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Mueve el foco al control de cuadro de diálogo anterior en el cuadro de diálogo.|  
|[CDialog::SetDefID](#setdefid)|Cambia el control de botón de comando predeterminado para un cuadro de diálogo a un botón de comando especificado.|  
|[CDialog::SetHelpID](#sethelpid)|Establece un identificador de ayuda contextual para el cuadro de diálogo.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|Reemplace este valor para realizar el botón Cancelar o la acción de la tecla ESC. El valor predeterminado cierra el cuadro de diálogo y **DoModal** devuelve **IDCANCEL**.|  
|[CDialog::OnOK](#onok)|Reemplace este valor para realizar la acción del botón Aceptar en el cuadro de diálogo modal. El valor predeterminado cierra el cuadro de diálogo y `DoModal` devuelve **IDOK**.|  
  
## <a name="remarks"></a>Comentarios  
 Cuadros de diálogo son de dos tipos: modales y no modales. Cuadro de diálogo modal debe cerrarse por el usuario antes de seguir con la aplicación. Un cuadro de diálogo no modal permite al usuario mostrar el cuadro de diálogo y volver a otra tarea sin cancelar o quitar el cuadro de diálogo.  
  
 A `CDialog` objeto es una combinación de una plantilla de cuadro de diálogo y un `CDialog`-clase derivada. Utilice el editor de cuadro de diálogo para crear la plantilla de cuadro de diálogo y almacenarlo en un recurso, a continuación, utilice el Asistente para agregar clases para crear una clase derivada de `CDialog`.  
  
 Un cuadro de diálogo, al igual que cualquier otra ventana, recibe los mensajes de Windows. En un cuadro de diálogo, están especialmente interesados en el tratamiento de mensajes de notificación de controles del cuadro de diálogo ya que es la forma en que el usuario interactúa con el cuadro de diálogo. Utilice la ventana Propiedades para seleccionar los mensajes que se va a identificador y agregará las entradas de mapa de mensajes adecuado y funciones de miembro de controlador de mensajes a la clase para usted. Solo tiene que escribir código específico de la aplicación en las funciones de miembro de controlador.  
  
 Si lo prefiere, que siempre podrá escribir las entradas del mapa de mensajes y las funciones miembro manualmente.  
  
 Salvo en el cuadro de diálogo más trivial, agregue variables miembro a la clase de cuadro de diálogo derivada para almacenar datos introducidos en los controles del cuadro de diálogo por el usuario o para mostrar los datos para el usuario. Puede usar al Asistente para agregar variables para crear variables de miembro y asociarlos con controles. Al mismo tiempo, elija un tipo de variable y el intervalo válido de valores para cada variable. El Asistente de código agrega las variables de miembro a la clase de cuadro de diálogo derivada.  
  
 Se genera un mapa de datos para controlar automáticamente el intercambio de datos entre las variables de miembro y los controles del cuadro de diálogo. La asignación de datos proporciona funciones que inicialice los controles en el cuadro de diálogo con los valores adecuados, recuperan los datos y validan los datos.  
  
 Para crear un cuadro de diálogo modal, construya un objeto en la pila utilizando el constructor para la clase de cuadro de diálogo derivada y, a continuación, llame a `DoModal` para crear el cuadro de diálogo y sus controles. Si desea crear un cuadro de diálogo no modal, llame a **crear** en el constructor de la clase de cuadro de diálogo.  
  
 También puede crear una plantilla en la memoria mediante una [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) estructura de datos, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Después de crear un `CDialog` objeto, llame a [CreateIndirect](#createindirect) para crear un no modal cuadro de diálogo o llamada [InitModalIndirect](#initmodalindirect) y [DoModal](#domodal) para crear un cuadro de diálogo modal.  
  
 La asignación de datos de exchange y la validación se escribe en un reemplazo del `CWnd::DoDataExchange` que se agrega a la nueva clase de cuadro de diálogo. Consulte la [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) función miembro en `CWnd` para obtener más información sobre la funcionalidad de intercambio y validación.  
  
 El programador y la llamada de framework `DoDataExchange` indirectamente a través de una llamada a [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).  
  
 Las llamadas de framework `UpdateData` cuando el usuario hace clic en el botón Aceptar para cerrar el cuadro de diálogo modal. (Los datos no se recuperan si se hace clic en el botón Cancelar). La implementación predeterminada de [OnInitDialog](#oninitdialog) también llama a `UpdateData` para establecer los valores iniciales de los controles. Normalmente se reemplaza `OnInitDialog` para inicializar los controles. `OnInitDialog`se llama después de que se crean todos los controles de cuadro de diálogo y justo antes del cuadro de diálogo se muestra el cuadro.  
  
 Puede llamar a `CWnd::UpdateData` en cualquier momento durante la ejecución de un cuadro de diálogo modal o no modal.  
  
 Si desarrolla un cuadro de diálogo a mano, agregue las variables miembro necesarios a la clase de cuadro de diálogo derivada usted mismo, y agregar funciones miembro para establecer u obtener estos valores.  
  
 Cuadro de diálogo modal cierra automáticamente cuando el usuario presione los botones Aceptar o cancelar o cuando el código llama a la `EndDialog` función miembro.  
  
 Cuando se implementa un cuadro de diálogo no modal, invalidar siempre la `OnCancel` función miembro y llame al método `DestroyWindow` desde dentro de él. No llame a la clase base `CDialog::OnCancel`, porque llama a `EndDialog`, lo que hará que el cuadro de diálogo invisible pero no se destruirán. También debe invalidar `PostNcDestroy` para los cuadros de diálogo no modal para eliminar **esto**, ya que normalmente se asignan a los cuadros de diálogo no modales **nueva**. Cuadros de diálogo modales se crean normalmente en el marco y no es necesario `PostNcDestroy` limpieza.  
  
 Para obtener más información sobre `CDialog`, vea:  
  
- [Cuadros de diálogo](../../mfc/dialog-boxes.md)  
  
-   El artículo de Knowledge Base Q262954: Cómo: crear un cuadro de diálogo tamaño ajustable con barras de desplazamiento  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cdialog"></a>CDialog::CDialog  
 Para construir un cuadro de diálogo modal basada en recursos, llame a cualquiera de las formas del constructor público.  
  
```  
explicit CDialog(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
explicit CDialog(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);  
  
CDialog();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
### <a name="remarks"></a>Comentarios  
 Un formulario del constructor proporciona acceso al recurso de cuadro de diálogo por nombre de la plantilla. El otro constructor proporciona acceso por número de identificación de plantilla, normalmente con un **IDD_** prefijo (por ejemplo, IDD_DIALOG1).  
  
 Para construir un cuadro de diálogo modal de una plantilla en la memoria, en primer lugar invocar el constructor sin parámetros, protegido y, a continuación, llamar a `InitModalIndirect`.  
  
 Después de crear un cuadro de diálogo modal con uno de los métodos anteriores, llame a `DoModal`.  
  
 Para construir un cuadro de diálogo no modales, utilice el formato protegido de la `CDialog` constructor. El constructor está protegido porque debe derivar su propia clase de cuadro de diálogo para implementar un cuadro de diálogo no modal. Construcción de un cuadro de diálogo no modal es un proceso de dos pasos. Llame primero al constructor; a continuación, llame a la **crear** función de miembro para crear un cuadro de diálogo basada en recursos, o llamar a `CreateIndirect` para crear el cuadro de diálogo desde una plantilla en la memoria.  
  
##  <a name="create"></a>CDialog::Create  
 Llame a **crear** para crear un cuadro de diálogo no modal mediante una plantilla de cuadro de diálogo desde un recurso.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTemplateName`  
 Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
 `nIDTemplate`  
 Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Ambas formas devuelven distinto de cero si la inicialización y la creación de cuadros de diálogo tuvo éxito; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede colocar la llamada a **crear** dentro del constructor o llamada se invoca después del constructor.  
  
 Dos formas de la **crear** función miembro se proporcionan para el acceso al recurso de plantilla de cuadro de diálogo Nombre de la plantilla o número de Id. de plantilla (por ejemplo, IDD_DIALOG1).  
  
 Para cualquiera de las formas, pasar un puntero al objeto de ventana primaria. Si `pParentWnd` es **NULL**, el cuadro de diálogo se creará con su ventana primaria o propietaria establecido en la ventana de la aplicación principal.  
  
 El **crear** función miembro devuelve inmediatamente después de crear el cuadro de diálogo.  
  
 Use la **WS_VISIBLE** aplicar un estilo en la plantilla de cuadro de diálogo si el cuadro de diálogo aparece cuando se crea la ventana primaria. En caso contrario, debe llamar a `ShowWindow`. Para obtener aún más los estilos de cuadro de diálogo y su aplicación, consulte el [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] y [estilos de ventana](../../mfc/reference/window-styles.md) en el *referencia de MFC*.  
  
 Use la `CWnd::DestroyWindow` función para destruir un cuadro de diálogo creado por el **crear** función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>CDialog::CreateIndirect  
 Llame a esta función miembro para crear un cuadro de diálogo no modal a partir de una plantilla de cuadro de diálogo en memoria.  
  
```  
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDialogTemplate`  
 Apunta a la memoria que contiene una plantilla de cuadro de diálogo que se utiliza para crear el cuadro de diálogo. Esta plantilla es en forma de un [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) información de estructura y el control, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria del objeto de cuadro de diálogo (de tipo [CWnd](../../mfc/reference/cwnd-class.md)). Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
 `lpDialogInit`  
 Apunta a un **DLGINIT** recursos.  
  
 `hDialogTemplate`  
 Contiene un identificador de memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla es en forma de un **DLGTEMPLATE** estructura y los datos para cada control en el cuadro de diálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el cuadro de diálogo se crea y se inicializa correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El `CreateIndirect` función miembro devuelve inmediatamente después de crear el cuadro de diálogo.  
  
 Use la **WS_VISIBLE** aplicar un estilo en la plantilla de cuadro de diálogo si el cuadro de diálogo aparece cuando se crea la ventana primaria. En caso contrario, debe llamar a `ShowWindow` para hacer que aparezca. Para obtener más información sobre cómo especificar otros estilos de cuadro de diálogo de la plantilla, consulte el [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) estructura en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Use la `CWnd::DestroyWindow` función para destruir un cuadro de diálogo creado por el `CreateIndirect` (función).  
  
 Cuadros de diálogo que contienen controles ActiveX requieren información adicional proporcionada en un **DLGINIT** recursos. Para obtener más información, vea el artículo de Knowledge Base Q231591, "Cómo: usar una plantilla de cuadro de diálogo para crear un cuadro de diálogo MFC con un ActiveX Control." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="domodal"></a>CDialog::DoModal  
 Llame a esta función miembro para invocar el cuadro de diálogo modal y devolver el resultado de cuadro de diálogo cuando haya finalizado.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `int` valor que especifica el valor de la `nResult` parámetro que se pasó a la [CDialog::EndDialog](#enddialog) función de miembro, que se utiliza para cerrar el cuadro de diálogo. El valor devuelto es -1 si la función no pudo crear el cuadro de diálogo o **IDABORT** si se ha producido algún otro error, en cuyo caso la ventana de resultados contendrá información de error de [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierra el cuadro de diálogo.  
  
 Si el usuario hace clic en uno de los botones de comando en el cuadro de diálogo, como Aceptar o cancelar, una función miembro de controlador de mensajes, como [OnOK](#onok) o [OnCancel](#oncancel), se llama para intentar cerrar el cuadro de diálogo. El valor predeterminado `OnOK` función miembro validar y actualizar los datos de cuadro de diálogo y cierre el cuadro de diálogo con el resultado **IDOK**y el valor predeterminado `OnCancel` función miembro cerrará el cuadro de diálogo con el resultado **IDCANCEL** sin validar o actualizar los datos de cuadro de diálogo. Puede invalidar estas funciones de controlador de mensajes para modificar su comportamiento.  
  
> [!NOTE]
> `PreTranslateMessage`Ahora se denomina para el procesamiento de mensajes del cuadro de diálogo modal.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>CDialog::EndDialog  
 Llame a esta función miembro para finalizar un cuadro de diálogo modal.  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `nResult`  
 Contiene el valor que se devuelve desde el cuadro de diálogo al llamador del `DoModal`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro devuelve `nResult` como el valor devuelto de `DoModal`. Debe utilizar el `EndDialog` función para completar el procesamiento cuando se crea un cuadro de diálogo modal.  
  
 Puede llamar a `EndDialog` en cualquier momento, incluso en [OnInitDialog](#oninitdialog), en cuyo caso debería cerrar el cuadro de diálogo antes de que se muestra o antes de establece el foco de entrada.  
  
 `EndDialog`no se cierre el cuadro de diálogo inmediatamente. En su lugar, Establece una marca que indica el cuadro de diálogo para cerrar tan pronto como vuelve el controlador de mensaje actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog #65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>CDialog::GetDefID  
 Llame a la `GetDefID` función de miembro para obtener el identificador del control de botón de comando predeterminado para un cuadro de diálogo.  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de 32 bits ( `DWORD`). Si el botón de comando predeterminado tiene un valor de identificador, la palabra de orden superior que contiene **DC_HASDEFID** y la palabra de orden inferior contiene el valor de identificador. Si el botón de comando predeterminado no tiene un valor de identificador, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser un botón de Aceptar.  
  
##  <a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl  
 Mueve el foco al control especificado en el cuadro de diálogo.  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndCtrl`  
 Identifica la ventana (control) que va a recibir el foco.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un puntero al control (ventana secundaria) para pasar como `pWndCtrl`, llame a la `CWnd::GetDlgItem` función de miembro, que devuelve un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).  
  
##  <a name="initmodalindirect"></a>CDialog:: InitModalIndirect  
 Llame a esta función miembro para inicializar un objeto de cuadro de diálogo modal mediante una plantilla de cuadro de diálogo que se construye en la memoria.  
  
```  
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDialogTemplate`  
 Apunta a la memoria que contiene una plantilla de cuadro de diálogo que se utiliza para crear el cuadro de diálogo. Esta plantilla es en forma de un [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) información de estructura y el control, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `hDialogTemplate`  
 Contiene un identificador de memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla es en forma de un **DLGTEMPLATE** estructura y los datos para cada control en el cuadro de diálogo.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) a la que pertenece el objeto de cuadro de diálogo. Si es **NULL**, ventana primaria del objeto de cuadro de diálogo se establece en la ventana de la aplicación principal.  
  
 `lpDialogInit`  
 Apunta a un **DLGINIT** recursos.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto de cuadro de diálogo se crea y se inicializa correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Para crear un cuadro de diálogo modal indirectamente, asignar un bloque de memoria global y rellenarlo con la plantilla de cuadro de diálogo. A continuación, llamar a vacío `CDialog` constructor para construir el objeto de cuadro de diálogo. A continuación, llame a `InitModalIndirect` para almacenar el identificador de la plantilla de cuadro de diálogo en memoria. Se crea y se muestra el cuadro de diálogo de Windows más adelante, cuando el [DoModal](#domodal) se llama la función miembro.  
  
 Cuadros de diálogo que contienen controles ActiveX requieren información adicional proporcionada en un **DLGINIT** recursos. Para obtener más información, vea el artículo de Knowledge Base Q231591, "Cómo: usar una plantilla de cuadro de diálogo para crear un cuadro de diálogo MFC con un ActiveX Control." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="mapdialogrect"></a>CDialog::MapDialogRect  
 La llamada para convertir las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) coordina el objeto que contiene el cuadro de diálogo va a convertir.  
  
### <a name="remarks"></a>Comentarios  
 Unidades de cuadro de diálogo se indican en términos de la unidad de base de cuadro de diálogo actual derivada del ancho medio y alto de caracteres de la fuente utilizada para el texto de cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de ancho de la base del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de alto de la base del cuadro de diálogo.  
  
 El **GetDialogBaseUnits** función de Windows devuelve información de tamaño de la fuente del sistema, pero puede especificar una fuente diferente para cada cuadro de diálogo si usas el **DS_SETFONT** estilo en el archivo de definición de recursos. El `MapDialogRect` la función de Windows usa la fuente adecuada para este cuadro de diálogo.  
  
 El `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo de `lpRect` con pantalla unidades (píxeles) para que el rectángulo se puede utilizar para crear un cuadro de diálogo o colocar un control dentro de un cuadro.  
  
##  <a name="nextdlgctrl"></a>CDialog::NextDlgCtrl  
 Mueve el foco al siguiente control en el cuadro de diálogo.  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si el foco está en el último control en el cuadro de diálogo, mueve al primer control.  
  
##  <a name="oncancel"></a>CDialog::OnCancel  
 El marco de trabajo llama a este método cuando el usuario hace clic en **cancelar** o presiona la tecla ESC en un cuadro de diálogo modal o no modal.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para llevar a cabo acciones (por ejemplo, para restaurar los datos antiguos) cuando un usuario cierra el cuadro de diálogo, haga clic en **cancelar** o presionar la tecla ESC. El valor predeterminado cierra el cuadro de diálogo modal mediante una llamada a [EndDialog](#enddialog) de archivo y provoquen [DoModal](#domodal) para devolver IDCANCEL.  
  
 Si implementa el **cancelar** botón en un cuadro de diálogo no modal, es necesario reemplazar el `OnCancel` método y llame al método [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No se llama al método de clase base, porque llama a `EndDialog`, que se haga el cuadro de diálogo invisible pero no destruirlo.  
  
> [!NOTE]
>  No se puede reemplazar este método cuando se usa un `CFileDialog` objeto en un programa compilado con Windows XP. Para obtener más información acerca de `CFileDialog`, consulte [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="oninitdialog"></a>CDialog:: OnInitDialog  
 Se llama a este método en respuesta a la `WM_INITDIALOG` mensaje.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica si la aplicación ha establecido el foco de entrada en uno de los controles en el cuadro de diálogo. Si `OnInitDialog` devuelve es distinto de cero, Windows establece el foco de entrada en la ubicación predeterminada, el primer control en el cuadro de diálogo. La aplicación puede devolver 0 solo si se establece explícitamente el foco de entrada a uno de los controles en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Windows envía la `WM_INITDIALOG` mensaje en el cuadro de diálogo durante la [crear](#create), [CreateIndirect](#createindirect), o [DoModal](#domodal) llamadas, que se producen inmediatamente antes de que se muestre el cuadro de diálogo.  
  
 Invalide este método si desea realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. En la versión reemplazada, llame primero a la clase base `OnInitDialog` pero que omita su valor devuelto. Normalmente devolverá `TRUE` desde el método invalidado.  
  
 Llamadas de Windows la `OnInitDialog` función mediante el procedimiento de cuadro de diálogo global estándar común a todos los cuadros de diálogo de biblioteca Microsoft Foundation Class. No se llama a esta función a través de la asignación de mensaje y, por lo tanto, no necesita una entrada de mapa de mensajes para este método.  
  
> [!NOTE]
>  No se puede reemplazar este método cuando se usa un `CFileDialog` objeto en un programa que se compila en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Para obtener más información sobre los cambios en `CFileDialog` en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] vea [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>CDialog::OnOK  
 Se llama cuando el usuario hace clic en el **Aceptar** botón (el botón con un Id. de IDOK).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para llevar a cabo acciones cuando el **Aceptar** se activa el botón. Si el cuadro de diálogo incluye el intercambio y validación de datos automática, la implementación predeterminada de este método valida los datos de cuadro de diálogo y actualiza las variables adecuadas en la aplicación.  
  
 Si implementa el **Aceptar** botón en un cuadro de diálogo no modal, es necesario reemplazar el `OnOK` método y llame al método [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No se llama al método de clase base, porque llama a [EndDialog](#enddialog) que hace que el cuadro de diálogo invisible pero destruirlo.  
  
> [!NOTE]
>  No se puede reemplazar este método cuando se usa un `CFileDialog` objeto en un programa compilado con Windows XP. Para obtener más información acerca de `CFileDialog`, consulte [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog #68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>CDialog::OnSetFont  
 Especifica la fuente que se va a usar un control de cuadro de diálogo al dibujar texto.  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFont`  
 Especifica un puntero a la fuente que se usará como la fuente predeterminada para todos los controles de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo usará la fuente especificada como el valor predeterminado para todos sus controles.  
  
 Normalmente, el editor de cuadro de diálogo establece la fuente del cuadro de diálogo como parte del recurso de plantilla de cuadro de diálogo.  
  
> [!NOTE]
>  No se puede reemplazar este método cuando se usa un `CFileDialog` objeto en un programa que se compila en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Para obtener más información sobre los cambios en `CFileDialog` en [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] vea [CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md).  
  
##  <a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl  
 Establece el foco al control anterior en el cuadro de diálogo.  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si el foco está en el primer control en el cuadro de diálogo, se desplaza hasta el último control en el cuadro.  
  
##  <a name="setdefid"></a>CDialog::SetDefID  
 Cambia el control de botón de comando predeterminado para un cuadro de diálogo.  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Especifica el identificador del control de botón de comando que se convertirá en el valor predeterminado.  
  
##  <a name="sethelpid"></a>CDialog::SetHelpID  
 Establece un identificador de ayuda contextual para el cuadro de diálogo.  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDR*  
 Especifica el identificador de ayuda contextual.  
  
## <a name="see-also"></a>Vea también  
 [DLGCBR32 de ejemplo MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC DLGTEMPL](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)


