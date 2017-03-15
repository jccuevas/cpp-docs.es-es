---
title: "Archivo (Men&#250; en una aplicaci&#243;n de base de datos MFC) | Microsoft Docs"
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
  - "menú Archivo"
  - "aplicaciones de base de datos [C++], comandos del menú Archivo"
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Archivo (Men&#250; en una aplicaci&#243;n de base de datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

¿Si crea una aplicación de base de datos MFC y no utiliza la serialización, cómo se debe interpretar el Abrir, cierre, el Guardar, y el Guardar como comandos en el menú archivo?  Aunque no hay instrucciones de estilo para esta pregunta, algunas sugerencias:  
  
-   Elimine el comando abierto desde el menú archivo completamente.  
  
-   Interpreta el comando que abiertas como “base de datos abierto” y mostrar el usuario una lista de orígenes de datos que la aplicación reconoce.  
  
-   Interpreta el comando abiertas como, quizás, “perfil abierto.” Mantenga el Abrir para abrir un archivo serializado, pero utiliza el archivo para almacenar un documento serializado que contiene información de “perfil de usuario”, como las preferencias del usuario, incluida su Id. de inicio de sesión \(opcionalmente excepto la contraseña\) y el origen de datos al mismo ejecutadas recientemente con.  
  
 El asistente para aplicaciones MFC permite crear una aplicación sin comandos de menú archivo relativos al documento.  Seleccione la opción de **Vista de base de datos sin compatibilidad con archivos** en la página de **Compatib. bases datos** .  
  
 Para interpretar un comando de menú archivo de una manera especial, debe reemplazar uno o más controladores de comandos, sobre todo en `CWinApp`\- clase derivada.  Por ejemplo, si invalida completamente `OnFileOpen` \(que implementa el comando de `ID_FILE_OPEN` \) para indicar la “base de datos abierto: ”  
  
-   No llame a la versión de la clase base de `OnFileOpen`, ya que reemplaza completamente la implementación predeterminada del marco de trabajo de comando.  
  
-   Utilice el controlador en su lugar para mostrar orígenes de datos de una lista del cuadro de diálogo.  Puede mostrar este diálogo llamando a `CDatabase::OpenEx` o `CDatabase::Open` con el parámetro **nulo**.  Se abrirá un cuadro de diálogo de ODBC que muestra todos los orígenes de datos disponibles en el equipo del usuario.  
  
-   Dado que las aplicaciones de base de datos no se guardan normalmente un documento entero, probablemente deseará quitar el Guardar y Guardar como implementaciones a menos que utilice un documento serializado para almacenar la información del perfil.  Si no, puede implementar el comando Save como, por ejemplo, “transacción de confirmación”. Vea [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) para obtener más información sobre cómo invalidar estos comandos.  
  
## Vea también  
 [Serialización: Serialización frente a entrada\/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md)