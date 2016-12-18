---
title: "WSADATA (Estructura) | Microsoft Docs"
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
  - "WSADATA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WSADATA (estructura)"
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WSADATA (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `WSADATA` se utiliza para almacenar la información de inicialización de Windows Sockets devuelta por una llamada a la función global de `AfxSocketInit` .  
  
## Sintaxis  
  
```  
  
      struct WSAData {  
   WORD wVersion;  
   WORD wHighVersion;  
   char szDescription[WSADESCRIPTION_LEN+1];  
   char szSystemStatus[WSASYSSTATUS_LEN+1];  
   unsigned short iMaxSockets;  
   unsigned short iMaxUdpDg;  
   char FAR * lpVendorInfo;  
};  
```  
  
#### Parámetros  
 *wVersion*  
 La versión de la especificación de Windows Sockets que el Windows Sockets DLL espera que el llamador utilice.  
  
 *wHighVersion*  
 La versión más alta de la especificación de Windows Sockets que esta DLL puede admitir \(también codificada como arriba\).  Normalmente, esto es lo mismo que **wVersion**.  
  
 *szDescription*  
 Una cadena ASCII terminada en null en la que el Windows Sockets DLL copia una descripción de la implementación de Windows Sockets, incluidos la identificación del proveedor.  El texto \(hasta 256 caracteres\) puede contener cualquier carácter, pero los proveedores se advierte con incluir caracteres de control y de formato: el uso más probable que una aplicación pondrá esto a es mostrarlo \(truncado posiblemente\) en un mensaje de estado.  
  
 *szSystemStatus*  
 Una cadena ASCII terminada en null en la que el Windows Sockets DLL copia el estado o la información de configuración pertinente.  El Windows Sockets DLL debe utilizar este campo solo si la información puede ser útil al usuario o el personal de soporte; no debe considerarse como extensión de campo de **szDescription** .  
  
 *iMaxSockets*  
 El número máximo de sockets que puede un único proceso potencialmente abierto.  Una implementación de Windows Sockets puede proporcionar un grupo global de sockets para la asignación a cualquier proceso; como alternativa, puede asignar los recursos de por\- proceso para sockets.  El número puede reflejar bien la manera en que el Windows Sockets DLL o el software de red se configuró.  Los programadores de aplicaciones pueden utilizar este número como indicación cruda de si la implementación de Windows Sockets es utilizable por la aplicación.  Por ejemplo, un servidor de X Windows podría comprobar **iMaxSockets** la primera vez que se inicie: si es menor que 8, la aplicación mostraría un mensaje de error que indica al usuario para reconfigurar el software de red. \(Esto es una situación en la que el texto de **szSystemStatus** podría utilizarse.\) Obviamente no hay ninguna garantía de que una aplicación determinada puede asignar realmente los sockets de **iMaxSockets** , ya que puede haber otras aplicaciones Windows Sockets en uso.  
  
 *iMaxUdpDg*  
 El tamaño en bytes del datagrama mayor de \(UDP\) de Protocolo de datagramas de usuario que se puede enviar o recibir mediante una aplicación de Windows Sockets.  Si la implementación no impone ningún límite, **iMaxUdpDg** es cero.  En muchas implementaciones de sockets de Berkeley, existe un límite implícitamente de 8192 bytes en los datagramas de UDP \(que se hace fragmentos si es necesario\).  Una implementación de Windows Sockets puede imponer un límite basado, por ejemplo, para la asignación de búferes de nuevo ensamble del fragmento.  El valor mínimo de **iMaxUdpDg** para una implementación en de Windows Sockets es 512.  Observe que independientemente del valor de **iMaxUdpDg**, es desaconsejable de intentar enviar un datagrama de difusión que sea mayor que la Unidad de transmisión máxima \(MTU\) para la red. \(El Windows Sockets API de no proporciona un mecanismo para detectar MTU, pero no debería ser menor de 512 bytes\).  
  
 *lpVendorInfo*  
 Un puntero lejano a una estructura de datos proveedor\- concreta.  La definición de esta estructura \(si se proporciona\) está fuera del ámbito de la especificación de Windows Sockets.  
  
> [!NOTE]
>  En MFC, la estructura de `WSADATA` es devuelta por la función de `AfxSocketInit` , que se llama a la función de `InitInstance` .  Puede recuperar la estructura y almacenarla en el programa si necesita usar información de ella más adelante.  
  
## Requisitos  
 **Encabezado:** winsock2.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../Topic/AfxSocketInit.md)