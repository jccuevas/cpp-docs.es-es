---
title: "Compatibilidad MAPI en MFC | Microsoft Docs"
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
  - "CDocument (clase), y MAPI"
  - "compatibilidad MAPI en MFC"
  - "MAPI, MFC"
  - "MFC, compatibilidad con MAPI"
  - "OnFileSendMail (método)"
  - "OnUpdateFileSendMail (método)"
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Compatibilidad MAPI en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compatibilidad con fuentes de MFC para un subconjunto de interfaz de programación de aplicaciones \(MAPI\) de mensajería de Microsoft en la clase **CDocument**.  Específicamente, **CDocument** tiene funciones miembro que determinan si la compatibilidad de correo está presente en el equipo del usuario final y, si es así habilita un comando de correo Send cuyo identificador estándar de comando es **ID\_FILE\_SEND\_MAIL**.  La función controladora de MFC para este comando permite al usuario enviar un documento a través de correo electrónico.  
  
> [!TIP]
>  Aunque MFC no encapsula el conjunto completo de la función MAPI, puede llamar a las funciones MAPI directamente, igual que pueden llamar a funciones de la API Win32 directamente de programas MFC.  
  
 Proporcionar el comando de correo Send en la aplicación es muy fácil.  MFC proporciona la implementación para empaquetar un documento \(es decir, **CDocument**\- objeto derivado\) como datos adjuntos y la envía como correo.  Estos datos adjuntos son equivalentes a un comando para guardar archivos que guarda \(serializa\) el contenido del documento al mensaje de correo.  Esta implementación llama al cliente de correo en el equipo del usuario para proporcionar al usuario la oportunidad de dirigir correo y agregar el asunto y el texto del mensaje al mensaje de correo.  Los usuarios ven la interfaz de usuario de la aplicación conocido de correo.  Esta funcionalidad se proporciona por dos funciones miembro de **CDocument** : `OnFileSendMail` y `OnUpdateFileSendMail`.  
  
 MAPI necesita leer el archivo para enviar los datos adjuntos.  Si la aplicación mantiene el archivo de datos abierto durante una llamada de función de `OnFileSendMail` , el archivo debe estar abierto con un modo de la acción que permite que varios procesos tengan acceso al archivo.  
  
> [!NOTE]
>  Una versión de reemplazo de `OnFileSendMail` para la clase `COleDocument` correctamente controla documentos compuestos.  
  
#### Para implementar un comando de correo Send con MFC  
  
1.  Utilice el editor de menús de Visual C\+\+ para agregar un elemento de menú cuyo identificador de comando es **ID\_FILE\_SEND\_MAIL**.  
  
     Este identificador de comando es proporcionada por el marco de trabajo en AFXRES.H.  El comando se puede agregar a cualquier menú, pero se agrega normalmente al menú de **archivo** .  
  
2.  Agregue manualmente el siguiente al mensaje de documento asignado:  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/CPP/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  Este mapa de mensajes funciona para un documento derivado de **CDocument** o de **COleDocument** — detecta la clase base correcta en cualquier caso, aunque el mapa de mensajes está en la clase derivada del documento.  
  
3.  Compile la aplicación.  
  
 Si la compatibilidad de correo está disponible, MFC permite el elemento de menú con `OnUpdateFileSendMail` y procesa posteriormente el comando con `OnFileSendMail`.  Si la compatibilidad de correo no está disponible, MFC automáticamente quita el elemento de menú para que el usuario no lo verá.  
  
> [!TIP]
>  En lugar de manualmente agregando el mensaje asignar las entradas como descrito anteriormente, puede utilizar la ventana Propiedades de la clase para asignar mensajes a funciones.  Para obtener más información, vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
 Para obtener información relacionada, vea información general de [MAPI](../mfc/mapi.md) .  
  
 Para obtener más información sobre el miembro de **CDocument** funciona ese permiso MAPI, vea:  
  
-   [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)  
  
-   [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)  
  
-   [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)  
  
## Vea también  
 [MAPI](../mfc/mapi.md)