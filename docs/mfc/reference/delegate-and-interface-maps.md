---
title: Interfaz y delegado asignan Macros (MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delegate map macros
- event map macros
- interface map macros
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
caps.latest.revision: 1
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
ms.sourcegitcommit: 9b6bd91f5fe02f3747a104be13b448d503af843c
ms.openlocfilehash: 51bf4627c8939a381ceaf14d51d05518b3859718
ms.contentlocale: es-es
ms.lasthandoff: 04/22/2017

---

|||  
|-|-|  
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Comienza una asignación de delegado.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Comienza la definición de la asignación interfaced.|
|[CommandHandler (delegado)](#commandhandler)|Registra los métodos de devolución de llamada con un origen de comando.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Finaliza un mapa de delegado.|
|[END_INTERFACE_MAP](#end_interface_map)|Finaliza el mapa de interfaz en el archivo de implementación. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crea una entrada en el mapa de delegado.|
|[INTERFACE_PART](#interface_part)|Utiliza entre el `BEGIN_INTERFACE_MAP` macro y `END_INTERFACE_MAP` por cada interfaz será compatible con el objeto.|
|[MAKE_DELEGATE](#make_delegate)|Asocia un controlador de eventos a un control administrado.|


## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP
Comienza una asignación de delegado.  
   
### <a name="syntax"></a>Sintaxis    
```  
BEGIN_DELEGATE_MAP(  CLASS );  
```
### <a name="parameters"></a>Parámetros  
 `CLASS`  
 La clase en la que se hospeda el control administrado.  
   
### <a name="remarks"></a>Comentarios  
 Esta macro marca el principio de una lista de entradas de delegado, que componen un mapa de delegado. Para obtener un ejemplo de cómo se utiliza esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** msclr\event.h  
   
### <a name="see-also"></a>Vea también  
 [Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)
 
##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP
Comienza la definición de la asignación de interfaced cuando se utiliza en el archivo de implementación.  
   
### <a name="syntax"></a>Sintaxis    
```
BEGIN_INTERFACE_MAP( theClass, baseClass )  
```
### <a name="parameters"></a>Parámetros  
 `theClass`  
 La clase en la que se debe definir el mapa de interfaz.  
  
 `baseClass`  
 La clase de la que `theClass` se deriva.  
   
### <a name="remarks"></a>Comentarios  
 Para cada interfaz que se implementa, hay uno o más `INTERFACE_PART` llamadas de macro. Para cada función de agregado que usa la clase, hay un **INTERFACE_AGGREGATE** llamada de macro.  
  
 Para obtener más información sobre los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
 
##  <a name="commandhandler"></a>CommandHandler (delegado)
Registra los métodos de devolución de llamada con un origen de comando.  
   
### <a name="syntax"></a>Sintaxis    
```  
delegate void CommandHandler(  UINT^ cmdID  );  
```
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando.  
   
### <a name="remarks"></a>Comentarios  
 Este delegado registra los métodos de devolución de llamada con un origen de comando. Cuando se agrega un delegado para el objeto de origen de comando, el método de devolución de llamada se convierte en un controlador para comandos procedentes del origen especificado.  
  
 Para obtener más información, consulte [Cómo: agregar el enrutamiento de comandos para el Control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h (definido en atlmfc\lib\mfcmifc80.dll ensamblado)  
   
### <a name="see-also"></a>Vea también  
 [Cómo: Agregar enrutamientos de comandos al control de Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)
 
##  <a name="commanduihandler"></a>CommandUIHandler
Registra los métodos de devolución de llamada con un mensaje de comando de actualización de interfaz de usuario.  
   
### <a name="syntax"></a>Sintaxis    
```  
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);  
```
### <a name="parameters"></a>Parámetros  
 `cmdID`  
 Identificador del comando.  
  
 `cmdUI`  
 El identificador de mensaje de comando.  
   
### <a name="remarks"></a>Comentarios  
 Este delegado registra los métodos de devolución de llamada con un mensaje de comando de actualización de interfaz de usuario. `CommandUIHandler`es similar a [CommandHandler](#commandhandler) salvo que este delegado se utiliza con los comandos de actualización de objeto de interfaz de usuario. Comandos de actualización de interfaz de usuario deben asignarse a uno a uno con los métodos de controlador de mensajes.  
  
 Para obtener más información sobre el uso de formularios Windows Forms, vea [mediante un Control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwinforms.h (definido en atlmfc\lib\mfcmifc80.dll ensamblado)  
   
### <a name="see-also"></a>Vea también  
 [Cómo: agregar comandos enrutamiento a Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP
Finaliza un mapa de delegado.  
   
### <a name="syntax"></a>Sintaxis    
```  
END_DELEGATE_MAP();  
```  
   
### <a name="remarks"></a>Comentarios  
 Esta macro marca el final de una lista de entradas de delegado, que componen un mapa de delegado. Para obtener un ejemplo de cómo se utiliza esta macro, consulte [EVENT_DELEGATE_ENTRY](#event_delegate_entry).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** msclr\event.h  
   
### <a name="see-also"></a>Vea también  

 [Cómo: Recibir eventos de Windows Forms de clases nativas de C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

 
##  <a name="end_interface_map"></a>END_INTERFACE_MAP
Finaliza el mapa de interfaz en el archivo de implementación.  
   
### <a name="syntax"></a>Sintaxis    
```
END_INTERFACE_MAP( )    
```  
   
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [BEGIN_INTERFACE_MAP](#begin_interface_map)
 

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY
Crea una entrada en el mapa de delegado.  
   
### <a name="syntax"></a>Sintaxis    
```  
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);  
```
### <a name="parameters"></a>Parámetros  
 `MEMBER`  
 El método de controlador de eventos para adjuntarlo al control.  
  
 `ARG0`  
 El primer argumento del método de controlador de evento administrado, como **objeto ^**.  
  
 `ARG1`  
 El segundo argumento del método de controlador de evento administrado, como **EventArgs ^**.  
   
### <a name="remarks"></a>Comentarios  
 Cada entrada de la asignación de delegado corresponde a un delegado de controlador de eventos administrados creado por [MAKE_DELEGATE](#make_delegate).  
   
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar `EVENT_DELEGATE_ENTRY` para crear una entrada en el mapa de delegado para la `OnClick` controlador de eventos; Vea también el ejemplo de código en `MAKE_DELEGATE`. Para obtener más información, consulte [Cómo: receptor de eventos de Windows Forms de clases de C++ nativo](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
 ```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()

```  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** msclr\event.h  
   
### <a name="see-also"></a>Vea también  
 [MAKE_DELEGATE](#make_delegate)   
 [BEGIN_DELEGATE_MAP](#begin_delegate_map)   
 [END_DELEGATE_MAP](#end_delegate_map)
 

##  <a name="interface_part"></a>INTERFACE_PART
Utiliza entre el `BEGIN_INTERFACE_MAP` macro y `END_INTERFACE_MAP` por cada interfaz será compatible con el objeto.  
   
### <a name="syntax"></a>Sintaxis    
```
INTERFACE_PART( theClass, iid, localClass)  
```
### <a name="parameters"></a>Parámetros  
 `theClass`  
 El nombre de la clase que contiene el mapa de interfaz.    
 `iid`  
 El IID que se puede asignar a la clase incrustada.    
 *localClass*  
 El nombre de la clase local.  
   
### <a name="remarks"></a>Comentarios  
 Permite asignar un IID a un miembro de la clase indicada por `theClass` y *localClass*.  
  
 Para obtener más información sobre los mapas de interfaz, vea [Nota técnica 38](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
   
 
##  <a name="make_delegate"></a>MAKE_DELEGATE
Asocia un controlador de eventos a un control administrado.  
   
### <a name="syntax"></a>Sintaxis    
```  
MAKE_DELEGATE( DELEGATE,  MEMBER) ;  
```
### <a name="parameters"></a>Parámetros  
 `DELEGATE`  
 Delegar el tipo del controlador de eventos administrados, como [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).  
  
 `MEMBER`  
 El nombre del método de controlador de eventos para adjuntarlo al control.  
   
### <a name="remarks"></a>Comentarios  
 Esta macro crea un delegado de controlador de evento administrado del tipo `DELEGATE` y del nombre `MEMBER`. El delegado del controlador de evento administrado permite que una clase nativa controlar los eventos administrados.  
   
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo llamar a `MAKE_DELEGATE` para adjuntar un `OnClick` controlador de eventos a un control MFC `MyControl`. Para obtener una explicación más amplia del funcionamiento de esta macro en una aplicación MFC, vea [Cómo: receptor de eventos de Windows Forms de clases de C++ nativo](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** msclr\event.h  
   
### <a name="see-also"></a>Vea también  
 [BEGIN_DELEGATE_MAP](#begin_delegate_map)   
 [END_DELEGATE_MAP](#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)
 




