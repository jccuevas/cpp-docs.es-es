---
title: "AFX_EXTENSION_MODULE (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AFX_EXTENSION_MODULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXTENSION_MODULE (estructura)"
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# AFX_EXTENSION_MODULE (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`AFX_EXTENSION_MODULE` se utiliza durante la inicialización de los archivos DLL de extensión MFC para contener el estado del módulo de DLL de extensión.  
  
## Sintaxis  
  
```  
  
      struct AFX_EXTENSION_MODULE  
{  
   BOOL bInitialized;  
   HMODULE hModule;  
   HMODULE hResource;  
   CRuntimeClass* pFirstSharedClass;  
   COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### Parámetros  
 *bInitialized*  
 **VERDADERO** si el módulo de DLL se ha inicializado con `AfxInitExtensionModule`.  
  
 `hModule`  
 Especifica el identificador de módulo de DLL.  
  
 *hResource*  
 Especifica el identificador de módulo personalizado de DLL.  
  
 *pFirstSharedClass*  
 Un puntero a información \(la estructura de `CRuntimeClass` \) a la primera clase en tiempo de ejecución del módulo de DLL.  Se utiliza para proporcionar el inicio de la lista de clases en tiempo de ejecución.  
  
 *pFirstSharedFactory*  
 Un puntero al generador del agente de DLL primero \(un objeto de `COleObjectFactory` \).  Se utiliza para proporcionar el inicio de la lista de generador de clases.  
  
## Comentarios  
 Los archivos DLL de extensión MFC necesitan realizar dos tareas en la función de `DllMain` :  
  
-   Llame a [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md) y compruebe el valor devuelto.  
  
-   Cree un objeto de **CDynLinkLibrary** si DLL exporta los objetos de [Recursos](../../mfc/reference/cruntimeclass-structure.md) o tiene sus propios recursos personalizados.  
  
 La estructura de `AFX_EXTENSION_MODULE` se utiliza para guardar una copia del estado del módulo de DLL de extensión, incluida una copia de los objetos de la clase en tiempo de ejecución que han sido se inicializan en el archivo DLL de extensión como parte de la construcción normal del objeto estático ejecute antes de que se entre `DllMain` .  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_1.cpp)]  
  
 La información de módulos almacenada en la estructura de `AFX_EXTENSION_MODULE` se puede copiar en el objeto de **CDynLinkLibrary** .  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/CPP/afx-extension-module-structure_2.cpp)]  
  
## Requisitos  
 **Header:** afx.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](../Topic/AfxInitExtensionModule.md)   
 [AfxTermExtensionModule](../Topic/AfxTermExtensionModule.md)