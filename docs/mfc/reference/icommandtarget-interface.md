---
title: Interfaz ICommandTarget | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b32112fbad516b2550da0cc48cb6c287583d396c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375582"
---
# <a name="icommandtarget-interface"></a>Interfaz ICommandTarget
Proporciona un control de usuario con una interfaz para recibir comandos de un objeto de origen de comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface class ICommandTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ICommandTarget:: Initialize](#initialize)|Inicializa el objeto de destino del comando.|  
  
## <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) comandos de rutas y actualización de comandos mensajes de interfaz de usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marco y botones de barra de herramientas). Implementando `ICommandTarget`, asigne el control de usuario de una referencia a la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objeto.  
  
 Vea [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h (definido en atlmfc\lib\mfcmifc80.dll ensamblado)  
  
##  <a name="initialize"></a> ICommandTarget:: Initialize  
 Inicializa el objeto de destino del comando.  
  
```  
void Initialize(ICommandSource^ cmdSource);  
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdSource`  
 Un identificador para el objeto de origen de comando.  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, CWinFormsView enruta los comandos y mensajes de interfaz de usuario de comandos de actualización para el control de usuario para permitirle controlar comandos MFC.  
  
 Este método inicializa el objeto de destino del comando y lo asocia con el cmdSource de objeto de origen de comando especificado. Se debe llamar en la implementación de la clase de control de usuario. En la inicialización, debe registrar los controladores de comandos con el objeto de origen de comando mediante ICommandSource::AddCommandHandler que realiza la llamada en la implementación de Initialize. Vea Cómo: agregar el enrutamiento de comandos para el Control de formularios Windows Forms para obtener un ejemplo de cómo usar Initialize para hacerlo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar comandos enrutamiento a Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandSource (interfaz)](../../mfc/reference/icommandsource-interface.md)



