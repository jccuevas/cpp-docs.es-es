---
title: Compatibilidad con MFC en ATL (proyectos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d42afec863695b1cab05c2d3cf2f65f3d64a1507
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360646"
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

