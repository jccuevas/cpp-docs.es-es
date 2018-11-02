---
title: Compatibilidad MAPI en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 564ce185758d25682a88f18a23b0b11afc84a4d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567158"
---
# <a name="mapi-support-in-mfc"></a>Compatibilidad MAPI en MFC

MFC proporciona compatibilidad con un subconjunto de la Microsoft aplicaciones de mensajería programa interfaz (MAPI) en la clase `CDocument`. En concreto, `CDocument` tiene funciones de miembro que determinen si la compatibilidad de correo está presente en el equipo del usuario final y, si es así, habilite un comando Enviar correo cuyo identificador de comando estándar sea ID_FILE_SEND_MAIL. La función de controlador MFC para este comando permite al usuario enviar un documento por correo electrónico.

> [!TIP]
>  Aunque MFC no encapsula todo el conjunto de función MAPI, todavía puede llamar funciones MAPI directamente, tal como se puede llamar a funciones de la API Win32 directamente desde programas MFC.

Proporcionar enviar correo comandos en la aplicación es muy fácil. MFC proporciona la implementación para empaquetar un documento (es decir, un `CDocument`-objeto derivado) como datos adjuntos y enviarlo por correo electrónico. Estos datos adjuntos están equivalente a un comando para guardar archivos que se guarda (serializa) el contenido del documento para el mensaje de correo. Esta implementación se llama cuando el cliente de correo electrónico en el equipo del usuario para proporcionar al usuario la oportunidad de dirección del mensaje y para agregar texto de asunto y el mensaje al mensaje de correo. Los usuarios ver la interfaz de usuario de la aplicación de su correo electrónico familiar. Esta funcionalidad se proporciona mediante dos `CDocument` funciones miembro: `OnFileSendMail` y `OnUpdateFileSendMail`.

MAPI se debe leer el archivo para enviar los datos adjuntos. Si la aplicación mantiene su archivo de datos abierto durante un `OnFileSendMail` llamada de función, el archivo debe abrirse con un modo de uso compartido que permite que varios procesos tener acceso al archivo.

> [!NOTE]
>  Una versión de reemplazo de `OnFileSendMail` para la clase `COleDocument` correctamente identificadores compuesta de documentos.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Para implementar un comando Enviar correo con MFC

1. Utilice el editor de menús de Visual C++ para agregar un elemento de menú cuyo identificador de comando sea ID_FILE_SEND_MAIL.

   Este identificador de comando se proporciona el marco de trabajo de AFXRES. H. El comando se puede agregar a cualquier menú, pero normalmente se agrega a la **archivo** menú.

1. Agregue manualmente lo siguiente al mapa de mensajes del documento:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Este mapa de mensajes funciona para un documento derivado de cualquiera `CDocument` o `COleDocument` : recoge la clase base correcta en cualquier caso, aunque el mapa de mensajes está en la clase derivada de documento.

1. Compile la aplicación.

Si está disponible la compatibilidad de correo, MFC permite que el elemento de menú con `OnUpdateFileSendMail` y después procesa el comando con `OnFileSendMail`. Si no está disponible la compatibilidad de correo, MFC quita automáticamente el elemento de menú para que el usuario no podrá visualizarlo.

> [!TIP]
>  En lugar de agregar manualmente las entradas de mapa de mensajes como se describió anteriormente, puede usar la ventana de propiedades de clase para asignar mensajes a funciones. Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

Para obtener información relacionada, consulte el [MAPI](../mfc/mapi.md) información general.

Para obtener más información sobre la `CDocument` funciones miembro que permiten MAPI, vea:

- [CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Vea también

[MAPI](../mfc/mapi.md)

