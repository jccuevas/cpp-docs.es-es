---
title: "Menú archivo en una aplicación de base de datos MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51f630f5a3fe1ee5833ac2796ff2acb1841af4c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="file-menu-in-an-mfc-database-application"></a>Archivo (Menú en una aplicación de base de datos MFC)
Si crea una aplicación de base de datos MFC y no utilizar la serialización, cómo debe interpretar abrir, cerrar, guardar y guardar como comandos en el menú archivo aunque no hay ninguna directriz de estilo para esta pregunta, estas son algunas sugerencias:  
  
-   Eliminar completamente el comando Abrir del menú archivo.  
  
-   Interprete el comando Abrir como "Abrir base de datos" y mostrar al usuario una lista de orígenes de datos que reconoce la aplicación.  
  
-   Interprete el comando Abrir como, quizás, "abrir perfil". Conservar abierto de pero abrir un archivo serializado, utilice el archivo para almacenar un documento serializado que contiene información de "perfil de usuario", como las preferencias del usuario, incluida su o su Id. de inicio de sesión (excluyendo opcionalmente la contraseña) y el origen de datos que más recientemente ha trabajado con.  
  
 El Asistente para aplicaciones MFC admite la creación de una aplicación con ningún comandos del menú archivo relacionados con el documento. Seleccione el **vista sin compatibilidad con archivos de base de datos** opción el **base de datos admite** página.  
  
 Para interpretar un comando del menú archivo de una manera especial, debe reemplazar uno o más controladores de comandos, principalmente en su `CWinApp`-clase derivada. Por ejemplo, si reemplaza completamente a `OnFileOpen` (que implementa el `ID_FILE_OPEN` comando) para indicar "Abrir base de datos:"  
  
-   No llame a la versión de la clase base de `OnFileOpen`, ya que se va a reemplazar completamente implementación de predeterminada del marco de trabajo del comando.  
  
-   Usar el controlador en su lugar, se muestra un cuadro de diálogo lista de orígenes de datos. Puede mostrar un cuadro de diálogo mediante una llamada a `CDatabase::OpenEx` o `CDatabase::Open` con el parámetro **NULL**. Se abrirá un cuadro de diálogo ODBC que muestra todos los orígenes de datos disponibles en el equipo del usuario.  
  
-   Dado que las aplicaciones de base de datos normalmente no guardan un documento completo, probablemente deseará quitar la operación de guardar y guardar como implementaciones a menos que utilice un documento serializado para almacenar información de perfil. De lo contrario, podría implementar el comando Guardar como, por ejemplo, "Confirmar transacción". Vea [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) para obtener más información sobre cómo reemplazar estos comandos.  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)

