---
title: "Control de la aplicación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- application control
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 81eb0bcdd8c9d154f62635e7f306cefcf7a15c1b
ms.lasthandoff: 02/24/2017

---
# <a name="application-control"></a>Control de la aplicación
OLE requiere un considerable control sobre las aplicaciones y sus objetos. La DLL del sistema OLE deben ser capaz de iniciar y lanzar aplicaciones automáticamente, coordinar su producción y la modificación de objetos y así sucesivamente. Las funciones de este tema cumplan dichos requisitos. Además de la DLL del sistema OLE que se llama, estas funciones deben llamarse a veces también las aplicaciones.  
  
### <a name="application-control"></a>Control de la aplicación  
  
|||  
|-|-|  
|[AfxOleCanExitApp](#afxolecanexitapp)|Indica si la aplicación puede finalizar.|  
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Recupera el filtro de mensajes de la aplicación actual.|  
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Recupera la marca de control de usuario actual.|  
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Establece o borra la marca de control de usuario.|  
|[AfxOleLockApp](#afxolelockapp)|Incrementa el recuento global del marco de trabajo del número de objetos activos en una aplicación.|  
|[AfxOleUnlockApp](#afxoleunlockapp)|Disminuye recuento del marco de trabajo del número de objetos activos en una aplicación.|  
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Registra un servidor en el registro del sistema OLE.|  
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementa la interfaz de usuario para la *typename* objeto de comando.|  
  
##  <a name="a-nameafxolecanexitappa--afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp  
 Indica si la aplicación puede finalizar.  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se puede salir de la aplicación; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación no debe finalizar si existen referencias pendientes a sus objetos. Las funciones globales `AfxOleLockApp` y `AfxOleUnlockApp` incremento y decremento, respectivamente, un contador de referencias a objetos de la aplicación. La aplicación no debe finalizar cuando este contador es distinto de cero. Si el contador es distinto de cero, la ventana principal de la aplicación se oculta (no destruido) cuando el usuario elija Cerrar en el menú de sistema o Exit en el menú archivo. El marco de trabajo llama a esta función **CFrameWnd::OnClose**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAutomation&#2;](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h 

##  <a name="a-nameafxolegetmessagefiltera--afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter  
 Recupera el filtro de mensajes de la aplicación actual.  
  
```   
COleMessageFilter* AFXAPI  AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero para el filtro de mensaje actual.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para obtener acceso a la actual `COleMessageFilter`-derivadas objeto, como se llamaría `AfxGetApp` para acceder al objeto de aplicación actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAutomation&3;](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation Nº&4;](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxwin.h 

##  <a name="a-nameafxolegetuserctrla--afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl  
 Recupera la marca de control de usuario actual.  
  
```   
BOOL  AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el usuario está en el control de la aplicación. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El usuario está en el control de la aplicación cuando el usuario ha abierto explícitamente o se crea un nuevo documento. El usuario también es en el control si la DLL del sistema OLE no inició la aplicación, es decir, si el usuario inicia la aplicación con el shell del sistema.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h

##  <a name="a-nameafxolesetuserctrla--afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl  
 Establece o borra la marca de control de usuario, que se explica en la referencia para `AfxOleGetUserCtrl`.  
  
```  
void  AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>Parámetros  
 *bUserCtrl*  
 Especifica si el indicador de control de usuario se va a establecer o borrar.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función cuando el usuario crea o carga un documento, pero no cuando se carga un documento o se creados a través de una acción indirecta, como la carga de un objeto incrustado desde una aplicación contenedora.  
  
 Llame a esta función si otras acciones en su aplicación deben colocar el usuario en el control de la aplicación.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h

##  <a name="a-nameafxolelockappa--afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp  
 Incrementa el recuento global del marco de trabajo del número de objetos activos en la aplicación.  
  
```   
void  AFXAPI  AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo mantiene un recuento del número de objetos activos en una aplicación. El `AfxOleLockApp` y `AfxOleUnlockApp` funciones, respectivamente, aumentar y disminuir este recuento.  
  
 Cuando el usuario intenta cerrar una aplicación que tiene objetos active, una aplicación para que el recuento de objetos activos es distinto de cero, el marco de trabajo oculta la aplicación desde la vista del usuario en lugar de apagarlo completamente. El `AfxOleCanExitApp` función indica si la aplicación puede finalizar.  
  
 Llame a `AfxOleLockApp` de cualquier objeto que expone interfaces OLE, si sería deseable para ese objeto se destruya mientras aún está en uso por una aplicación cliente. Llamar a `AfxOleUnlockApp` en el destructor de cualquier objeto que llama a `AfxOleLockApp` en el constructor. De forma predeterminada, `COleDocument` (y sus clases derivadas) bloquear y desbloquear la aplicación automáticamente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAutomation&#5;](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h

##  <a name="a-nameafxoleunlockappa--afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp  
 Disminuye recuento del marco de trabajo de objetos activos en la aplicación.  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte `AfxOleLockApp` para obtener más información.  
  
 Cuando el número de objetos activos llega a cero, **AfxOleOnReleaseAllObjects** se llama.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [AfxOleLockApp](#afxolelockapp).  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h  

##  <a name="a-nameafxoleregisterserverclassa--afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass  
 Esta función permite registrar el servidor en el registro del sistema OLE.  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `clsid`  
 Referencia al Id. de servidor OLE  
  
 `lpszClassName`  
 Puntero a una cadena que contiene el nombre de la clase de objetos del servidor.  
  
 *lpszShortTypeName*  
 Puntero a una cadena que contiene el nombre corto del tipo de objeto del servidor, como "Gráfico".  
  
 *lpszLongTypeName*  
 Puntero a una cadena que contiene el nombre largo del tipo de objeto del servidor, como "Gráfico de Microsoft Excel 5.0."  
  
 `nAppType`  
 Un valor, tomado de la **OLE_APPTYPE** enumeración, que especifica el tipo de aplicación OLE. Los valores posibles son los siguientes:  
  
- `OAT_INPLACE_SERVER`Servidor tiene interfaz de usuario de servidor completo.  
  
- `OAT_SERVER`Servidor admite únicamente la incrustación.  
  
- `OAT_CONTAINER`Contenedor admite vínculos con incrustaciones.  
  
- `OAT_DISPATCH_OBJECT``IDispatch`-objeto capaz.  
  
 `rglpszRegister`  
 Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE si no existentes para las claves se encuentran valores.  
  
 `rglpszOverwrite`  
 Matriz de punteros a cadenas que representan las claves y valores que se agregarán al registro del sistema OLE si el registro contiene los valores existentes para las claves especificadas.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la clase de servidor se ha registrado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar la mayoría de las aplicaciones **COleTemplateServer::Register** para registrar los tipos de documento de la aplicación. Si el formato de registro del sistema de la aplicación no ajusta el patrón típico, puede usar `AfxOleRegisterServerClass` para obtener más control.  
  
 El registro se compone de un conjunto de claves y valores. El `rglpszRegister` y `rglpszOverwrite` argumentos son matrices de punteros a cadenas, que consta de una clave y valor separan por un **NULL** caracteres ( `'\0'`). Cada una de estas cadenas puede tener parámetros reemplazables cuyos lugares marcados por las secuencias de caracteres `%1` a través de `%5`.  
  
 Los símbolos se rellenan como sigue:  
  
|Símbolo|Valor|  
|------------|-----------|  
|%1|Id. de clase con formato de cadena|  
|%2|Nombre de la clase|  
|%3|Ruta de acceso al archivo ejecutable|  
|%4|Nombre de tipo corto|  
|%5|Nombre de tipo Long|  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h

##  <a name="a-nameafxoleseteditmenua--afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu  
 Implementa la interfaz de usuario para la *typename* objeto de comando.  
  
```   
void  AFXAPI  AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pClient`  
 Un puntero al elemento de cliente OLE.  
  
 `pMenu`  
 Un puntero al objeto de menú para actualizarse.  
  
 *iMenuItem*  
 El índice del elemento de menú para actualizarse.  
  
 `nIDVerbMin`  
 El identificador de comando que se corresponde con el verbo principal.  
  
 *nIDVerbMax*  
 El identificador de comando que corresponde al último verbo.  
  
 *nIDConvert*  
 Id. del elemento de menú de Convert.  
  
### <a name="remarks"></a>Comentarios  
 Si el servidor reconoce solo un verbo principal, se convierte en el elemento de menú "verbo *typename* objeto" y el `nIDVerbMin` comando se envía cuando el usuario elige el comando. Si el servidor reconoce varios verbos, entonces se convierte en el elemento de menú " *typename* objeto" y un submenú que enumera todos los verbos aparece cuando el usuario elige el comando. Cuando el usuario elige un verbo en el submenú, `nIDVerbMin` se envía si se elige el primer verbo, `nIDVerbMin` + 1 se envía si el segundo verbo está seleccionado y así sucesivamente. El valor predeterminado `COleDocument` implementación controla automáticamente esta característica.  
  
 Debe tener la siguiente instrucción de script de recursos de aplicación de su cliente (. Archivo RC):  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxole.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

