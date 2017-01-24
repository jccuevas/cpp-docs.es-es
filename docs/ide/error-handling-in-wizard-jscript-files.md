---
title: "Control de errores en los archivos JScript del asistente | Microsoft Docs"
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
  - "control de errores, JScript"
  - "JScript, controlar errores"
  - "control de errores de JScript en asistentes"
ms.assetid: 6df3ba46-7ab6-484c-ac45-b08f4b6a5900
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de errores en los archivos JScript del asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un asistente, el proyecto incluye los archivos Default.js y Common.js.  Estos archivos se utilizan para personalizar los proyectos.  Vea [El archivo JScript](../ide/jscript-file.md) para obtener más información.  
  
 En todo proyecto se debería incluir algún procedimiento de control de errores.  El siguiente código proporciona un ejemplo de dicho control de errores.  
  
### Control de errores en JScript  
  
1.  Para detectar errores en el momento en que el usuario hace clic en **Finalizar**, escriba el siguiente código:  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       try  
       {  
          .....  
       }  
       catch(e)  
       {  
          if (e.description.length != 0)  
             SetErrorInfo(e.description, e.number);  
          return e.number  
       }  
    }  
    ```  
  
2.  Produzca `e` desde cualquier función auxiliar de script utilizada en el script:  
  
    ```  
    function ExtenderFromType(strVariableType)  
    {  
       try  
       {  
          ....  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
3.  Si el parámetro **PREPROCESS\_FUNCTION** está en el [archivo .vsz](../ide/dot-vsz-file-project-control.md), el asistente llama a [CanAddATLClass](../ide/jscript-functions-for-cpp-wizards.md).  En caso de error, utilice [SetErrorInfo](../ide/seterrorinfo.md) y devuelva **false**:  
  
    ```  
    function CanAddATLClass(oProj, oObject)  
    {  
       try  
       {  
          if (!IsATLProject(oProj))  
          {  
             if (!IsMFCProject(oProj, true))  
             {     
                var L_CanAddATLClass_Text = "ATL classes can only be added  
     to ATL, MFC EXE and MFC regular DLL projects.";  
                wizard.ReportError(L_CanAddATLClass_Text);  
                return false;  
             }  
             else  
             {  
                .....  
                var bRet = AddATLSupportToProject(oProj);  
                .....  
                return bRet;  
             }  
          }  
          return true;  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
4.  Si ha de volver al cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**, devuelva **VS\_E\_WIZBACKBUTTONPRESS**:  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       ....  
       if (!CheckAddtoProject(selProj))  
       {  
          return VS_E_WIZARDBACKBUTTONPRESS;  
       }  
    }  
    ```  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [Personalizar un asistente](../ide/customizing-your-wizard.md)