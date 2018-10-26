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
ms.openlocfilehash: ad9e55fa296b8a39e4c77ab33240c837b6c871ea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063502"
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

