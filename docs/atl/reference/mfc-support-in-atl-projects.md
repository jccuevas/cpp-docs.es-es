---
title: "Compatibilidad con MFC en proyectos ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.atl.addmfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, compatibilidad con MFC"
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Compatibilidad con MFC en proyectos ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si selecciona **Admitir MFC** en el Asistente para proyectos ATL, el proyecto declarará la aplicación como un objeto de aplicación MFC \(clase\).  El proyecto inicializa la biblioteca MFC y crea una instancia de una clase \(la clase *Nombre\_proyecto*\) derivada de [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Esta opción sólo está disponible para proyectos de archivo DLL sin atributos.  
  
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
  
 Puede ver la clase de objeto de aplicación y sus funciones `InitInstance` y `ExitInstance` en la Vista de clases.  
  
## Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)