---
title: "Interfaz ICommandTarget | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ICommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Interfaz ICommandTarget"
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# Interfaz ICommandTarget
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona un control de usuario con una interfaz para recibir comandos de un objeto de origen de comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface class ICommandTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ICommandTarget:: Initialize](#icommandtarget__initialize)|Inicializa el objeto de destino del comando.|  
  
## <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) rutas comandos y actualizar mensajes de interfaz de Usuario para el control de usuario para que pueda controlar los comandos MFC (por ejemplo, elementos de menú de marcos y botones de barra de herramientas) del comando. Implementando `ICommandTarget`, asigne el control de usuario de una referencia a la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objeto.  
  
 Vea [Cómo: agregar el enrutamiento de comandos para el Control Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) para obtener un ejemplo de cómo usar `ICommandTarget`.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h (definido en el ensamblado atlmfc\lib\mfcmifc80.dll)  
  
##  <a name="a-nameicommandtargetinitializea-icommandtargetinitialize"></a><a name="icommandtarget__initialize"></a> ICommandTarget:: Initialize  
 Inicializa el objeto de destino del comando.  
  
```  
void Initialize(ICommandSource^ cmdSource);

 
```  
  
### <a name="parameters"></a>Parámetros  
 `cmdSource`  
 Un identificador para el objeto de origen de comando.  
  
### <a name="remarks"></a>Comentarios  
 Al hospedar un control de usuario en una vista de MFC, CWinFormsView enruta los comandos y mensajes de interfaz de Usuario de comandos de actualización para el control de usuario para permitirle controlar comandos MFC.  
  
 Este método inicializa el objeto de destino del comando y lo asocia con el cmdSource de objeto de origen de comando especificado. Se debe llamar en la implementación de la clase de control de usuario. En la inicialización, debe registrar controladores de comandos con el objeto de origen de comando por llamada ICommandSource::AddCommandHandler en la implementación de la inicialización. Vea Cómo: agregar el enrutamiento de comandos para el Control de formularios Windows Forms para obtener un ejemplo de cómo utilizar Initialize para hacerlo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar comandos enrutamiento a Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [Interfaz de ICommandSource](../../mfc/reference/icommandsource-interface.md)



