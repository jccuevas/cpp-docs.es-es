---
title: "TN028: Compatibilidad con la ayuda contextual | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.help"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Ayuda contextual, MFC (aplicaciones)"
  - "identificadores de recursos, Ayuda contextual"
  - "TN028"
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN028: Compatibilidad con la ayuda contextual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe las reglas para asignar e id. de otros contextos de Ayuda problemas de ayuda en MFC.  Compatibilidad de ayuda contextual requiere el compilador de la ayuda que está disponible en Visual C\+\+.  
  
> [!NOTE]
>  Además de implementar ayuda contextual mediante WinHelp, MFC también permite utilizar ayuda HTML.  Para obtener más información sobre esta compatibilidad y la programación con ayuda de HTML, vea [Ayuda HTML: Ayuda contextual para programas de The](../mfc/html-help-context-sensitive-help-for-your-programs.md).  
  
## Tipos de Ayuda admitidos  
 Hay dos tipos de ayuda contextual implementados en aplicaciones Windows.  El primer, denominado “Ayuda de F1” implica iniciar de WinHelp con el contexto correcto basado en el objeto activo.  El segundo es “modo de F1 de Shift\+”.  En este modo, los cambios del cursor del mouse en la ayuda cursor, y el usuario continúa para hacer clic en un objeto.  En ese momento, WinHelp se inicia para proporcionar ayuda para el objeto que el usuario hace clic en.  
  
 La implementación de Microsoft Foundation Classes dos formas de ayuda.  Además, el marco admite dos comandos de ayuda, índices de Ayuda y la ayuda simples de Utilizar.  
  
## Archivos de Ayuda  
 Las clases base de Microsoft suponen un único archivo de Ayuda.  El archivo de Ayuda debe tener el mismo nombre y ruta de acceso que la aplicación.  Por ejemplo, si el archivo ejecutable es C:\\MyApplication\\MyHelp.exe el archivo de ayuda debe ser C:\\MyApplication\\MyHelp.hlp.  Establezca la ruta de acceso a través de la variable miembro de `m_pszHelpFilePath` de [CWinApp Class](../mfc/reference/cwinapp-class.md).  
  
## Intervalos de contexto de Ayuda  
 La implementación predeterminada de MFC requiere un programa realizar algunas reglas sobre la asignación de los id. de contexto de Ayuda.  Estas reglas son un intervalo de los id. asignados a controles específicos.  Puede reemplazar estas reglas proporcionando implementaciones diferentes de las diversas funciones AYUDA\- relacionadas de miembro.  
  
```  
0x00000000 - 0x0000FFFF : user defined  
0x00010000 - 0x0001FFFF : commands (menus/command buttons)  
   0x00010000 + ID_  
   (note: 0x18000-> 0x1FFFF is the practical range since command IDs are >=0x8000)  
0x00020000 - 0x0002FFFF : windows and dialogs  
   0x00020000 + IDR_  
   (note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)  
0x00030000 - 0x0003FFFF : error messages (based on error string ID)  
   0x00030000 + IDP_  
0x00040000 - 0x0004FFFF : special purpose (non-client areas)  
   0x00040000 + HitTest area  
0x00050000 - 0x0005FFFF : controls (those that are not commands)  
   0x00040000 + IDW_  
```  
  
## Comandos simples de “Ayuda”  
 Existen dos comandos simples de Ayuda implementados por Microsoft Foundation Classes:  
  
-   ID\_HELP\_INDEX implementado por [CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)  
  
-   ID\_HELP\_USING implementado por [CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)  
  
 El primer comando muestra el índice de la Ayuda de la aplicación.  El segundo muestra la ayuda del usuario sobre el uso del programa de WinHelp.  
  
## Ayuda contextual \(Ayuda de F1\)  
 F1 es traducida normalmente a un comando con un identificador de `ID_HELP` por un acelerador activo en la tabla de aceleradores de la ventana principal.  El comando de `ID_HELP` también se puede generar mediante un botón con un identificador de `ID_HELP` en la ventana principal o el cuadro de diálogo.  
  
 Independientemente de cómo se genera el comando de `ID_HELP` , se distribuye como un comando normal hasta alcanzar un controlador de comandos.  Para obtener más información acerca de la arquitectura de comando\- enrutamiento de MFC, vea la [Nota técnica 21](../mfc/tn021-command-and-message-routing.md).  Si la aplicación tiene Ayuda habilitada, [CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)controlará el comando de `ID_HELP` .  El objeto application recibe el mensaje de ayuda y después distribuye el comando correctamente.  Esto es necesario porque el enrutamiento predeterminado del comando no es adecuado para determinar el contexto más concreto.  
  
 intentos de`CWinApp::OnHelp` de iniciar WinHelp en el orden siguiente:  
  
1.  Comprueba una llamada activo de `AfxMessageBox` con un identificador de Ayuda  Si un cuadro de mensaje está actualmente activa, WinHelp se inicia al contexto adecuado en ese cuadro de mensaje.  
  
2.  Envía un mensaje de WM\_COMMANDHELP a la ventana activa.  Si esa ventana no responde iniciando WinHelp, el mismo mensaje se envía a los antecesores de esa ventana hasta que se procesa el mensaje o la ventana actual es una ventana de nivel superior.  
  
3.  Envía un comando de ID\_DEFAULT\_HELP a la ventana principal.  Esto invoca la Ayuda predeterminada.  Asignados a este comando normalmente a `CWinApp::OnHelpIndex`.  
  
 Para global invalidar los valores base predeterminados ID \(por ejemplo 0x10000 para comandos y 0x20000 para los recursos como cuadros de diálogo\), la aplicación debe reemplazar [CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md).  
  
 Para evitar esta funcionalidad y la forma en que un contexto de Ayuda se determina, debe controlar el mensaje de WM\_COMMANDHELP.  Puede proporcionar un enrutamiento más específico de Ayuda que el marco de trabajo proporciona, como va tan profundamente como ventana secundaria actual de MDI.  Puede que también desee proporcionar una ayuda más específica para una ventana o un diálogo determinada, quizás basada en el estado interno actual del objeto o control activo dentro del diálogo.  
  
## WM\_COMMANDHELP  
  
```  
  
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
```  
  
 WM\_COMMANDHELP es un mensaje privado de Windows MFC que es recibido por la ventana activa cuando se solicita la Ayuda.  Cuando la ventana recibe este mensaje, puede llamar a `CWinApp::WinHelp` con el contexto que coincide con el estado interno de la ventana.  
  
 `lParam`  
 Contiene el contexto actualmente disponibles de Ayuda.  `lParam` es cero si no se ha determinado ningún contexto de Ayuda.  Una implementación de `OnCommandHelp` puede utilizar el Id. de contexto en `lParam` para determinar un contexto diferente o simplemente puede pasarlo a `CWinApp::WinHelp`.  
  
 `wParam`  
 No se utiliza y será cero.  
  
 Si la función llama `CWinApp::WinHelp`, no de `OnCommandHelp` devuelven `TRUE`.  Devolver `TRUE` detiene el enrutamiento de este comando a otras clases y a otras ventanas.  
  
## Modo de Ayuda \(Ayuda Shift\+F1\)  
 Éste es el segundo formulario de ayuda contextual.  Normalmente, presionando entra en este modo MAYÚS\+F1 o mediante el menú o la barra de herramientas.  Se implementa como un comando \(**ID\_CONTEXT\_HELP**\).  No utilizan el enlace del filtro de mensajes para traducir este comando como un cuadro de diálogo o un menú modal está activo, por consiguiente este comando solo está disponible al usuario cuando la aplicación se está ejecutando el suministro principal de mensajes \(`CWinApp::Run`\).  
  
 Después de entrar en este modo, el cursor de Ayuda se muestra información sobre todas las áreas de la aplicación, incluso si la aplicación mostraría normalmente su propio cursor para esa área \(como el borde de cambio de tamaño alrededor de la ventana\).  El usuario puede utilizar el mouse o el teclado para seleccionar un comando.  En lugar de ejecutar el comando, la Ayuda de ese comando se muestra.  Además, el usuario puede hacer clic en un objeto visible en la pantalla, como un botón en la barra de herramientas, y se mostrará la Ayuda para ese objeto.  `CWinApp::OnContextHelp`proporciona este modo de Ayuda.  
  
 Durante la ejecución de este bucle, toda la entrada de teclado está inactiva, excepto las teclas que tienen acceso al menú.  Además, la traducción de comando aún se realiza mediante `PreTranslateMessage` para permitir que el usuario presione una tecla de aceleración y recibir ayuda en ese comando.  
  
 Si hay traducciones determinadas o funcionan las acciones que tienen lugar en `PreTranslateMessage` que no debe aplicarse durante el modo de Ayuda MAYÚS\+F1, debe comprobar el miembro de `m_bHelpMode` de `CWinApp` antes de realizar estas operaciones.  La implementación de `CDialog` de `PreTranslateMessage` comprueba esto antes de llamar a `IsDialogMessage`, por ejemplo.  Esto deshabilita “las teclas de navegación de diálogo” en cuadros de diálogo no modal durante el modo MAYÚS\+F1.  Además, `CWinApp::OnIdle` todavía se denomina durante este bucle.  
  
 Si el usuario elige un comando de menú, se trata como ayuda en ese comando \(con **WM\_COMMANDHELP**, vea a continuación\).  Si el usuario hace clic en un área visible de la ventana de las aplicaciones, se crea una determinación de si es un clic de no cliente o un clic del cliente.  la asignación de identificadores de`OnContextHelp` de no cliente hace clic en el cliente hace clic automáticamente.  Si es un clic del cliente, envía **WM\_HELPHITTEST** a la ventana que se ha hecho clic.  Si esa ventana devuelve un valor distinto de cero, ese valor se usa como el contexto de ayuda.  Si devuelve cero, `OnContextHelp` intenta la ventana primaria \(y no es el caso, el elemento primario, etc.\).  Si un contexto de Ayuda no puede ser determinado, el valor predeterminado es enviar un comando de **ID\_DEFAULT\_HELP** a la ventana principal, que a continuación \(normalmente\) se asigna a `CWinApp::OnHelpIndex`.  
  
## WM\_HELPHITTEST  
  
```  
  
afx_msg LRESULT CWnd::OnHelpHitTest(  
WPARAM, LPARAM lParam)  
```  
  
 **WM\_HELPHITTEST** es un mensaje privado de las ventanas de MFC que es recibido por la ventana activa hizo clic durante el modo de Ayuda MAYÚS\+F1.  Cuando la ventana recibe este mensaje, devuelve un identificador de Ayuda de DWORD para uso de WinHelp.  
  
 LOWORD \(lParam\)  
 contiene las coordenadas de dispositivo del eje X donde se hizo clic con el mouse en relación con el área de cliente de la ventana.  
  
 HIWORD \(lParam\)  
 contiene la coordenada del eje Y.  
  
 `wParam`  
 no se utiliza y será cero.  Si el valor devuelto es cero, WinHelp lleva ese contexto.  Si el valor devuelto es cero, la ventana primaria se consulta para obtener ayuda.  
  
 En muchos casos, puede aprovechar las ventajas de código de la prueba de posicionamiento que puede contar.  Vea la implementación de **CToolBar::OnHelpHitTest** para obtener un ejemplo de administrar el mensaje de **WM\_HELPHITTEST** \(el código aprovecha el código de la prueba de posicionamiento utilizado en los botones y la información sobre herramientas en `CControlBar`\).  
  
## Compatibilidad con el asistente para aplicaciones MFC y MAKEHM  
 El Asistente para aplicaciones MFC crea los archivos necesarios para compilar un archivo de Ayuda \(archivos de .cnt y de .hpj\).  También incluye varios archivos preintegrada .rtf que sean aceptados por el compilador de ayuda de Microsoft.  Muchos de los temas se completa, pero algunos deban modificarse para la aplicación concreta.  
  
 La creación automática “de un archivo de asignación de ayuda” es admitida por una utilidad denominada MAKEHM.  La utilidad MAKEHM puede traducir el archivo de RESOURCE.H de una aplicación a un archivo de asignación de Ayuda.  Por ejemplo:  
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 se traducirá a:  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 Este formato es compatible con la utilidad del compilador de Ayuda, que asigna los id. de contexto \(números en el lado derecho\) con los nombres de tema \(los símbolos en el lado izquierdo\).  
  
 El código fuente de MAKEHM está disponible en MFC que programa el ejemplo [MAKEHM](../top/visual-cpp-samples.md)de utilidades.  
  
## Agregando Ayuda Después admiten que ejecuta el asistente para aplicaciones MFC  
 La mejor manera de agregar Ayuda a la aplicación es comprobar la opción de “ayuda contextual” en la página avanzada de las características del Asistente para aplicaciones MFC antes de crear la aplicación.  De esta manera el asistente para aplicaciones MFC automáticamente agrega las entradas necesarias a `CWinApp`\- clase derivada del mapa de mensajes a la Ayuda compatible con.  
  
## Ayuda sobre los cuadros de mensaje  
 La Ayuda sobre los cuadros de mensaje \(a veces denominado alertas\) es compatible con la función de `AfxMessageBox` , un contenedor de la API de Windows `MessageBox` .  
  
 Hay dos versiones de `AfxMessageBox`, de uno para su uso con un identificador de cadena y otra para el uso con un puntero a la cadena \(`LPCSTR`\):  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText, UINT nType, UINT nIDHelp);  
int AFXAPI AfxMessageBox(UINT nIDPrompt, UINT nType, UINT nIDHelp);  
```  
  
 En ambos casos, hay un identificador opcional de Ayuda  
  
 En el primer caso, el valor predeterminado para el nIDHelp es 0, que no indica ninguna Ayuda para este mensaje.  Si el usuario presiona F1 mientras como el cuadro de mensaje está activo, el usuario no recibirá Ayuda \(incluso si la aplicación admite Ayuda\).  Si no es deseable, un identificador de Ayuda se debe proporcionar para el nIDHelp.  
  
 En el segundo caso, el valor predeterminado para el nIDHelp es \-1, que indica que el identificador de Ayuda es igual que nIDPrompt.  Ayuda sólo funcionará si AYUDA\- se habilita la aplicación, por supuesto\).  Debe proporcionar 0 para el nIDHelp si desea que el cuadro de mensaje no tiene compatibilidad de ayuda.  Si desea que el mensaje para ser Ayuda habilitada, pero desea un identificador diferente de ayuda que nIDPrompt, proporcione simplemente un valor positivo para el nIDHelp diferente del de nIDPrompt.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)