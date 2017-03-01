---
title: Clase CWinFormsDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsDialog
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- CWinFormsDialog class
- Windows Forms [C++], MFC support
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
caps.latest.revision: 26
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
ms.openlocfilehash: 86768a849b0112f7c4f8b6b2a694b80065169575
ms.lasthandoff: 02/24/2017

---
# <a name="cwinformsdialog-class"></a>Clase CWinFormsDialog
Un contenedor para una clase de cuadro de diálogo MFC que hospeda un control de usuario de formularios Windows Forms.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TManagedControl`  
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
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicializa el cuadro de diálogo MFC crea y aloja un control de usuario de formularios Windows Forms en ella.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Convierte un tipo de una referencia a un control de usuario de formularios Windows Forms.|  
  
## <a name="remarks"></a>Comentarios  
 `CWinFormsDialog`es un contenedor para una clase de cuadro de diálogo MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) que hospeda un control de usuario de formularios Windows Forms. Esto permite la visualización de los controles de .NET Framework en un cuadro de diálogo MFC modal o no modal.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) y [hospedar un Control de usuario de Windows Forms como un cuadro de diálogo de MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h  
  
##  <a name="a-namecwinformsdialoga--cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog  
 Construye un objeto `CWinFormsDialog`.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDTemplate`  
 Contiene el identificador de un recurso de plantilla de cuadro de diálogo. Utilice el editor de cuadro de diálogo para crear la plantilla de cuadro de diálogo y almacenarlo en el archivo de script de recursos de la aplicación. Para obtener más información sobre las plantillas de cuadro de diálogo, vea [CDialog (clase)](../../mfc/reference/cdialog-class.md).  
  
##  <a name="a-namegetcontrola--cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::GetControl  
 Recupera una referencia al control de usuario de formularios Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al control de formularios Windows Forms en el cuadro de diálogo MFC.  
  
##  <a name="a-namegetcontrolhandlea--cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle  
 Recupera un identificador de ventana para el control de usuario de formularios Windows Forms.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador de ventana para el control de usuario de formularios Windows Forms.  
  
##  <a name="a-nameoninitdialoga--cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog  
 Inicializa el cuadro de diálogo MFC crea y aloja un control de usuario de formularios Windows Forms en ella.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que especifica si la aplicación ha establecido el foco de entrada a uno de los controles en el cuadro de diálogo. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada al primer control en el cuadro de diálogo. Este método puede devolver 0 sólo si la aplicación establece explícitamente el foco de entrada a uno de los controles en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea el cuadro de diálogo MFC (mediante el [crear](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), o [DoModal](../../mfc/reference/cdialog-class.md#domodal) método hereda de [CDialog](../../mfc/reference/cdialog-class.md)), un `WM_INITDIALOG` envía el mensaje y se llama a este método. Crea una instancia de un control de formularios Windows Forms en el cuadro de diálogo y ajusta el tamaño del cuadro de diálogo para acomodar el tamaño del control de usuario. A continuación, aloja el nuevo control en el cuadro de diálogo MFC.  
  
 Reemplace esta función miembro si necesita realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. Para obtener más información acerca de cómo utilizar este método, consulte [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).  
  
##  <a name="a-nameoperator-gta--cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::operator-&gt;  
 Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador proporciona una sintaxis adecuada que reemplaza `GetControl` en expresiones.  
  
 Para obtener información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="a-nameoperatortmanagedcontrolxora--cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol_xor"></a>CWinFormsDialog::operator TManagedControl ^  
 Convierte un tipo de una referencia a un control de usuario de formularios Windows Forms.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador convierte un tipo de una referencia a un control de formularios Windows Forms. Se utiliza para pasar un `CWinFormsDialog<``TManagedControl``>` cuadro de diálogo para las funciones que aceptan un puntero a un objeto de control de usuario de formularios Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Clase CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)

