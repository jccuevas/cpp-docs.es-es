---
title: Compatibilidad con MFC en proyectos ATL | Microsoft Docs
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
ms.openlocfilehash: f3853bbe90757563f6c7dc2c9003ed7c5f2a98dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065444"
---
# <a name="mfc-support-in-atl-projects"></a>Compatibilidad con MFC en proyectos ATL

Si selecciona **compatibilidad con MFC** en el Asistente para proyectos ATL, el proyecto declara la aplicación como un objeto de aplicación MFC (clase). El proyecto se inicializa la biblioteca MFC y crea una instancia de una clase (clase *Nombre_proyecto*) que se deriva [CWinApp](../../mfc/reference/cwinapp-class.md).

Esta opción está disponible para proyectos DLL ATL sin atributos solo.

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

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)

