---
title: "Puntos de entrada de funciones exportadas de un archivo DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exportar archivos DLL, funciones"
  - "MFC, administrar datos de estado"
  - "administración de estados, archivos DLL exportados"
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Puntos de entrada de funciones exportadas de un archivo DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para las funciones exportadas desde el archivo DLL, utilice la macro de [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) para mantener el estado global adecuada al cambiar de módulo de DLL a DLL de la aplicación de llamada.  
  
 Cuando se llama, esta macro establece `pModuleState`, un puntero a una estructura de `AFX_MODULE_STATE` que contiene los datos globales del módulo, como el estado real del módulo para el resto del ámbito contenedor de la función.  Sobre dejar el ámbito que contiene la macro, se restablece el estado efectiva anterior de módulo automáticamente.  
  
 Esta conmutación se logra construyendo una instancia de una clase de **AFX\_MODULE\_STATE** en la pila.  En el constructor, esta clase obtiene un puntero al estado actual del módulo y lo almacena en una variable miembro, y establezca `pModuleState` como el nuevo estado real del módulo.  En su destructor, esta clase restablece el puntero almacenado en la variable miembro como el estado real del módulo.  
  
 Si tiene una función exportada, como una que inicia un cuadro de diálogo en un archivo DLL, necesita agregar el código siguiente al principio de la función:  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/CPP/exported-dll-function-entry-points_1.cpp)]  
  
 Esto cambia al estado actual del módulo con el estado devuelto de [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md) hasta el final del ámbito actual.  
  
 Los problemas con recursos en archivos DLL aparecerán si la macro de `AFX_MANAGE_STATE` no se utiliza.  De forma predeterminada, MFC utiliza el identificador de recursos de la aplicación principal para cargar la plantilla de recursos.  Esta plantilla se almacena realmente en el archivo DLL.  La principal causa es que la información de estado del módulo MFC no ha sido intercambiada por la macro de `AFX_MANAGE_STATE` .  El identificador de recursos se recupera del estado del módulo de MFC.  No cambiar el estado de módulo hace que el identificador de recursos incorrecto que se utilizará.  
  
 `AFX_MANAGE_STATE` no necesita estar en cada función en el archivo DLL.  Por ejemplo, `InitInstance` puede llamar al código MFC en la aplicación sin `AFX_MANAGE_STATE` MFC se desplaza automáticamente al estado del módulo antes de `InitInstance` y de modificadores se vuelve después de que `InitInstance` vuelva.  Lo mismo se aplica a todos los controladores de mensaje\- mapa.  Los archivos DLL estándar incluyen realmente un procedimiento de ventana principal especial que automáticamente cambie el estado del módulo antes de enviar cualquier mensaje.  
  
## Vea también  
 [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)