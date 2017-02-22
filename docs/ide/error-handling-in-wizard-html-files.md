---
title: "Control de errores en los archivos HTML del asistente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de errores, comprobación de errores en archivos"
  - "HTML, control de errores"
ms.assetid: eb428a64-b681-4420-987d-92098bf98455
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Control de errores en los archivos HTML del asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un asistente con interfaz de usuario, el proyecto incluye archivos .htm.  Estos archivos se utilizan para personalizar los proyectos.  Vea [Los archivos HTML](../ide/html-files.md) para obtener más información.  
  
 En todo proyecto se debería incluir algún procedimiento de control de errores.  El siguiente código proporciona un ejemplo de dicho control de errores.  
  
### Control de errores en HTML  
  
1.  Al validar los campos, si llama a un método de validación de una DLL \(donde debería establecerse la información sobre errores\), deberá llamar sin parámetros a `ReportError`.  
  
    ```  
    function ValidateInput()  
    {  
       if (!window.external.ValidateFile(HEADER_FILE.value))  
       {  
          ReportError();  
          HEADER_FILE.focus();  
          return false;  
       }  
    }  
    ```  
  
2.  Al validar campos, si los valida sólo con el script HTML, deberá llamar primero a `SetErrorInfo` y, a continuación, a `ReportError` sin parámetros.  
  
    ```  
    function OnWhatever()  
    {  
       if (!ValidateInput())  
          window.external.ReportErrror();  
       ....  
    }  
  
    function ValidateInput()  
    {  
       .....  
  
       if (HEADER_FILE.value == IMPL_FILE.value)  
       {  
          var L_ErrMsg_Text = "Header and implementation files cannot have the same name.";  
          SetErrorInfo(L_ErrMsg_Text);  
          bValid = false;  
       }  
       if (TYPE.value == "")  
       {  
          var L_ErrMsg4_Text = "Type cannot be blank.";  
          SetErrorInfo(L_ErrMsg4_Text);  
          bValid = false;  
       }  
       return bValid;  
    }  
    ```  
  
3.  Llame con parámetros a `ReportError`:  
  
    ```  
    function ValidateInput()  
    {  
       if (!IsListed(strType))  
       {  
          var L_Invalid2_Text = "The variable type should be one of the types listed.";  
          window.external.ReportError(L_Invalid2_Text);  
          VariableType.focus();  
          return false;  
       }  
    }  
    ```  
  
4.  Si ha de volver al cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**, devuelva **VS\_E\_WIZBACKBUTTONPRESS**:  
  
    ```  
    try  
    {  
       oCM   = window.external.ProjectObject.CodeModel;  
    }  
    catch(e)  
    {  
       var L_NCBError_Text = "Cannot access the Class View information   
    file. Class View information will not be available.";  
       window.external.ReportError(L_NCBError_Text);  
       return VS_E_WIZARDBACKBUTTONPRESS;  
    ```  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [Personalizar un asistente](../ide/customizing-your-wizard.md)