---
title: WSADATA (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WSADATA
dev_langs:
- C++
helpviewer_keywords:
- WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dadc502900285d879f2fd77af69b1fcf08a4ba1e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880936"
---
# <a name="wsadata-structure"></a>WSADATA (Estructura)
El `WSADATA` estructura se usa para almacenar información de inicialización de Windows Sockets devuelto por una llamada a la `AfxSocketInit` función global.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 *wVersion*  
 La versión de la especificación Windows Sockets que la DLL de Windows Sockets se espera que el llamador utilice.  
  
 *wHighVersion*  
 La versión más alta de la especificación Windows Sockets que puede admitir este archivo DLL (también se codifican como arriba). Normalmente, esto equivale a *wVersion*.  
  
 *szDescription*  
 Una cadena ASCII terminada en null en la que la DLL de Windows Sockets copia una descripción de la implementación de Windows Sockets, incluida la identificación del proveedor. El texto (hasta 256 caracteres de longitud) puede contener cualquier carácter, pero se recomienda proveedores no incluido el control y caracteres de formato: el uso más probable que una aplicación se pondrán a es para que se muestre (posiblemente truncado) en un mensaje de estado.  
  
 *szSystemStatus*  
 Una cadena ASCII terminada en null en la que la DLL de Windows Sockets copia información de estado o configuración relevante. La DLL de Windows Sockets deben usar este campo sólo si la información podría resultar útil al usuario o admite personal; no debe considerarse como una extensión de la *szDescription* campo.  
  
 *iMaxSockets*  
 El número máximo de sockets que potencialmente puede abrir un único proceso. Una implementación de Windows Sockets puede proporcionar un grupo global de sockets para la asignación a cualquier proceso; como alternativa, puede asignar recursos por proceso para los sockets. El número también puede reflejar la manera en que se ha configurado la DLL de Windows Sockets o el software de red. Los escritores de aplicaciones pueden utilizar este número como una indicación de si la implementación de Windows Sockets es utilizable por la aplicación rudimentario. Por ejemplo, puede comprobar un servidor de Windows X *iMaxSockets* cuando se inicia por primera vez: si es menor que 8, la aplicación mostrará un mensaje de error que indica al usuario volver a configurar el software de red. (Esta es una situación en la que el *szSystemStatus* podría utilizarse el texto.) Obviamente, no hay ninguna garantía de que realmente puede asignar una aplicación determinada *iMaxSockets* sockets, dado que puede haber otras aplicaciones de Windows Sockets en uso.  
  
 *iMaxUdpDg*  
 El tamaño en bytes del datagrama más grande de protocolo de datagramas de usuario (UDP) que puede ser enviados o recibidos por una aplicación de Windows Sockets. Si la implementación no impone ningún límite, *iMaxUdpDg* es cero. En muchas implementaciones de sockets de Berkeley, hay un límite implícito de 8192 bytes en datagramas UDP (que están fragmentados si es necesario). Una implementación de Windows Sockets puede imponer un límite basado, por ejemplo, en la asignación de búferes reensamblado de fragmento. El valor mínimo de *iMaxUdpDg* para un Sockets de Windows compatible con la implementación es 512. Tenga en cuenta que, independientemente del valor de *iMaxUdpDg*, no es recomendable intentar enviar un datagrama de difusión es mayor que la unidad de transmisión máxima (MTU) para la red. (La API de Windows Sockets no proporciona un mecanismo para detectar la MTU, pero debe ser no menos de 512 bytes).  
  
 *lpVendorInfo*  
 Un puntero lejano a una estructura de datos específicos del proveedor. La definición de esta estructura (si se proporciona) está fuera del ámbito de la especificación Windows Sockets.  
  
> [!NOTE]
>  En MFC, la `WSADATA` estructura devuelta por la `AfxSocketInit` función, que se llama en su `InitInstance` función. Puede recuperar la estructura y almacenarlo en el programa si tiene que utilizar la información más adelante.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winsock2.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)

