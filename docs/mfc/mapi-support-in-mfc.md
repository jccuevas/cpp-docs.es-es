---
title: Compatibilidad MAPI en MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 301e15b11b05f9ccbeaee63aead486f1cc6c405c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931907"
---
# <a name="mapi-support-in-mfc"></a>Compatibilidad MAPI en MFC
MFC proporciona compatibilidad con un subconjunto de la Microsoft aplicaciones de mensajería programa interfaz (MAPI) en la clase `CDocument`. En concreto, `CDocument` tiene las funciones de miembro que determinan si la compatibilidad de correo está presente en el equipo del usuario final y, si es así, permite un comando Enviar correo cuyo identificador de comando estándar sea ID_FILE_SEND_MAIL. La función de controlador MFC para este comando permite al usuario enviar un documento por correo electrónico.  
  
> [!TIP]
>  Aunque MFC no encapsula el conjunto completo de funciones MAPI, se pueden seguir llamando a funciones MAPI directamente, tal y como se puede llamar a funciones de la API de Win32 directamente desde programas MFC.  
  
 Proporcionar enviar correo comandos en la aplicación es muy fácil. MFC proporciona la implementación para empaquetar un documento (es decir, un `CDocument`-objeto derivado) como datos adjuntos y enviarlo por correo electrónico. Están equivalente a un comando guardado de archivo que guarda estos datos adjuntos (serializa) el contenido del documento al mensaje de correo. Esta implementación se llama cuando el cliente de correo electrónico en el equipo del usuario para conceder al usuario la oportunidad de dirección del mensaje y para agregar texto de asunto y el mensaje al mensaje de correo. Los usuarios ver la interfaz de usuario de su aplicación de correo electrónico familiarizado. Esta funcionalidad se proporciona por dos `CDocument` funciones miembro: `OnFileSendMail` y `OnUpdateFileSendMail`.  
  
 MAPI debe leer el archivo para enviar los datos adjuntos. Si la aplicación mantiene su archivo de datos abierto durante un `OnFileSendMail` llamada de función, el archivo debe abrirse con un modo de uso compartido que permite que varios procesos tener acceso al archivo.  
  
> [!NOTE]
>  Una versión de reemplazo de `OnFileSendMail` para la clase `COleDocument` correctamente identificadores compuestos documentos.  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Implementar un comando Enviar correo con MFC  
  
1.  Utilice el editor de menús de Visual C++ para agregar un elemento de menú cuyo identificador de comando sea ID_FILE_SEND_MAIL.  
  
     Este identificador de comando se proporciona el marco de trabajo de AFXRES. H. El comando puede agregarse a cualquier menú, pero normalmente se agrega a la **archivo** menú.  
  
2.  Agregue manualmente lo siguiente al mapa de mensajes del documento:  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  Este mapa de mensajes funcionará para un documento derivado de uno `CDocument` o `COleDocument` : recoge la clase base correcta en cualquier caso, aunque el mapa de mensajes está en la clase derivada de documento.  
  
3.  Compile su aplicación.  
  
 Si está disponible la compatibilidad con el correo, MFC habilita el elemento de menú con `OnUpdateFileSendMail` y después procesa el comando con `OnFileSendMail`. Si no hay compatibilidad con el correo, MFC quita automáticamente el elemento de menú para que el usuario no podrán visualizar.  
  
> [!TIP]
>  En lugar de agregar manualmente las entradas de mapa de mensajes como se describió anteriormente, puede usar la ventana de propiedades de clase para asignar mensajes a funciones. Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
 Para obtener información relacionada, consulte el [MAPI](../mfc/mapi.md) información general.  
  
 Para obtener más información sobre la `CDocument` funciones miembro que permiten MAPI, vea:  
  
-   [CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument:: OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>Vea también  
 [MAPI](../mfc/mapi.md)

