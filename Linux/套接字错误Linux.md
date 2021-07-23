

|Error Code|描述|
|:-------------|:---------------|
|EACCES| For Unix domain sockets, which are identified by pathname: Write permission is denied on the socket file, or search permission is denied for one of the directories in the path prefix. (See also path_resolution(2).)|
|EACCES, EPERM|The user tried to connect to a broadcast address without having the socket broadcast flag enabled or the connection request failed because of a local firewall rule.|
|EADDRINUSE|Local address is already in use.|
|EAFNOSUPPORT|The passed address didn’t have the correct address family in itssa_family field.|
|EADDRNOTAVAIL|Non-existent interface was requested or the requested address was not local.|
|EALREADY|The socket is non-blocking and a previous connection attempt has not yet been completed.|
|EBADF| The file descriptor is not a valid index in the descriptor table.|
|ECONNREFUSED|No one listening on the remote address.|
|EFAULT|The socket structure address is outside the user’s address space.|
|EINPROGRESS|The socket is non-blocking and the connection cannot be completed immediately. It is possible to select(2) or poll(2) for completion by selecting the socket for writing. After select(2) indicates writability, use getsockopt(2) to read the SO_ERRORoption at level SOL_SOCKET to determine whether connect() completed successfully (SO_ERROR is zero) or unsuccessfully (SO_ERROR is one of the usual error codes listed here, explaining the reason for the failure).|
|EINTR|The system call was interrupted by a signal that was caught.|
|EISCONN|The socket is already connected.|
|ENETUNREACH| Network is unreachable.|
|ENOTSOCK|The file descriptor is not associated with a socket.|
|ETIMEDOUT|Timeout while attempting connection. The server may be too busy to accept new connections. Note that for IP sockets the timeout may be very long when syncookies are enabled on the server.|
