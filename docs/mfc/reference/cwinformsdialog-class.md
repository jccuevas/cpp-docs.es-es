---
title: Clase CWinFormsDialog | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7596140f48b62a63189444bee6fb363552766fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Construye un objeto `CWinFormsDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|Recupera una referencia al control de usuario de formularios Windows Forms.|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Recupera un identificador de ventana para el control de usuario de formularios Windows Forms.|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicializa el cuadro de diálogo MFC mediante la creación y hospedar un control de usuario de formularios Windows Forms en ella.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|nombre||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Convierte un tipo como una referencia a un control de usuario de formularios Windows Forms.|  
  
## <a name="remarks"></a>Comentarios  
 `CWinFormsDialog` es un contenedor para una clase de cuadro de diálogo MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) que hospeda un control de usuario de formularios Windows Forms. Esto permite la visualización de los controles de .NET Framework en un cuadro de diálogo MFC modal o no modal.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) y [hospedar un Control de usuario de Windows Forms como un cuadro de diálogo de MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 Construye un objeto `CWinFormsDialog`.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDTemplate`  
 Contiene el identificador de un recurso de plantilla de cuadro de diálogo. Utilice el editor de cuadro de diálogo para crear la plantilla de cuadro de diálogo y almacenarlo en el archivo de script de recursos de la aplicación. Para obtener más información sobre plantillas de cuadro de diálogo, vea [CDialog (clase)](../../mfc/reference/cdialog-class.md).  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 Recupera una referencia al control de usuario de formularios Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al control de formularios Windows Forms en el cuadro de diálogo MFC.  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 Recupera un identificador de ventana para el control de usuario de formularios Windows Forms.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador de ventana para el control de usuario de formularios Windows Forms.  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 Inicializa el cuadro de diálogo MFC mediante la creación y hospedar un control de usuario de formularios Windows Forms en ella.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que especifica si la aplicación ha establecido el foco de entrada en uno de los controles en el cuadro de diálogo. Si `OnInitDialog` devuelve es distinto de cero, Windows establece el foco de entrada para el primer control en el cuadro de diálogo. Este método puede devolver 0 sólo si la aplicación establece explícitamente el foco de entrada a uno de los controles en el cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea el cuadro de diálogo MFC (mediante el [crear](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), o [DoModal](../../mfc/reference/cdialog-class.md#domodal) método se hereda de [CDialog](../../mfc/reference/cdialog-class.md)), un `WM_INITDIALOG` se envía el mensaje y se llama a este método. Crea una instancia de un control de formularios Windows Forms en el cuadro de diálogo y ajusta el tamaño del cuadro de diálogo para dar cabida a para el tamaño del control de usuario. A continuación, hospeda el nuevo control en el cuadro de diálogo MFC.  
  
 Reemplace esta función miembro si tiene que realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. Para obtener más información sobre cómo utilizar este método, consulte [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 Reemplaza [CWinFormsDialog::GetControl](#getcontrol) en expresiones.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador proporciona una sintaxis adecuada que reemplaza `GetControl` en expresiones.  
  
 Para obtener información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 Convierte un tipo como una referencia a un control de usuario de formularios Windows Forms.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este operador convierte un tipo como una referencia a un control de formularios Windows Forms. Se utiliza para pasar un `CWinFormsDialog<TManagedControl>` cuadro de diálogo para las funciones que aceptan un puntero a un objeto de control de usuario de formularios Windows Forms.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Clase CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)
