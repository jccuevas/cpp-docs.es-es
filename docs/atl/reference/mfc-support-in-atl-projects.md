---
title: Compatibilidad con MFC en ATL (proyectos) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.atl.addmfc
dev_langs: C++
helpviewer_keywords: ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 399f9fcea216adf5480bf38b8aba051c60eed496
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-support-in-atl-projects"></a>Compatibilidad con MFC en ATL (proyectos)
Si selecciona **compatibilidad con MFC** en el Asistente para proyectos ATL, el proyecto declarará la aplicación como un objeto de aplicación MFC (clase). El proyecto inicializa la biblioteca MFC y crea una instancia de una clase (clase *Nombre_proyecto*) que se deriva de [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Esta opción está disponible para proyectos ATL DLL sin atributos solo.  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
 
// Overrides  
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP() 
};  
 
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
 
CProjNameApp theApp;  
 
BOOL CProjNameApp::InitInstance()  
{  
    return CWinApp::InitInstance();

}  
 
int CProjNameApp::ExitInstance()  
{  
    return CWinApp::ExitInstance();

}  
```  
  
 Puede ver la clase de objeto de aplicación y su `InitInstance` y `ExitInstance` funciones en la vista de clases.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

