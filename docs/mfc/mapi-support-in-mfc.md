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
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356997"
---
# <a name="mapi-support-in-mfc"></a>Compatibilidad MAPI en MFC

MFC proporciona compatibilidad con un subconjunto de la interfaz de `CDocument`programa de aplicación de mensajería de Microsoft (MAPI) en la clase . En concreto, `CDocument` tiene funciones miembro que determinan si la compatibilidad con correo está presente en el equipo del usuario final y, si es así, habilita un comando Enviar correo cuyo identificador de comando estándar está ID_FILE_SEND_MAIL. La función de controlador MFC para este comando permite al usuario enviar un documento a través de correo electrónico.

> [!TIP]
> Aunque MFC no encapsula todo el conjunto de funciones MAPI, todavía puede llamar a funciones MAPI directamente, del igual que puede llamar a funciones de API Win32 directamente desde programas MFC.

Proporcionar el comando Enviar correo en la aplicación es muy fácil. MFC proporciona la implementación para empaquetar `CDocument`un documento (es decir, un objeto derivado) como datos adjuntos y enviarlo como correo. Este archivo adjunto es equivalente a un comando Guardar archivo que guarda (serializa) el contenido del documento en el mensaje de correo. Esta implementación llama al cliente de correo en el equipo del usuario para dar al usuario la oportunidad de dirigir el correo y agregar el asunto y el texto del mensaje al mensaje de correo. Los usuarios ven la interfaz de usuario de su aplicación de correo familiar. Esta funcionalidad se proporciona `CDocument` mediante `OnFileSendMail` dos `OnUpdateFileSendMail`funciones miembro: y .

MAPI necesita leer el archivo para enviar los datos adjuntos. Si la aplicación mantiene su `OnFileSendMail` archivo de datos abierto durante una llamada de función, el archivo debe abrirse con un modo de recurso compartido que permita que varios procesos accedan al archivo.

> [!NOTE]
> Una versión `OnFileSendMail` de `COleDocument` reemplazo de para la clase maneja correctamente los documentos compuestos.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Para implementar un comando Enviar correo con MFC

1. Utilice el editor de menús de Visual C++ para agregar un elemento de menú cuyo identificador de comando es ID_FILE_SEND_MAIL.

   Este identificador de comando lo proporciona el marco de trabajo en AFXRES. H. El comando se puede agregar a cualquier menú, pero normalmente se agrega al menú **Archivo.**

1. Agregue manualmente lo siguiente al mapa de mensajes del documento:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Este mapa de mensajes funciona para `CDocument` `COleDocument` un documento derivado de una o — recoge la clase base correcta en cualquier caso, aunque el mapa de mensajes está en la clase de documento derivada.

1. Compile la aplicación.

Si la compatibilidad con correo está `OnUpdateFileSendMail` disponible, MFC habilita `OnFileSendMail`el elemento de menú con y, posteriormente, procesa el comando con . Si la compatibilidad con correo no está disponible, MFC quita automáticamente el elemento de menú para que el usuario no lo vea.

> [!TIP]
> En lugar de agregar manualmente entradas de mapa de mensajes como se describió anteriormente, puede usar el [Asistente para](reference/mfc-class-wizard.md) clases de clase para asignar mensajes a funciones. Para obtener más información, consulte Asignación de [mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

Para obtener información relacionada, vea la información general de [MAPI.](../mfc/mapi.md)

Para obtener más `CDocument` información acerca de las funciones miembro que habilitan MAPI, vea:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Consulte también

[MAPI](../mfc/mapi.md)
