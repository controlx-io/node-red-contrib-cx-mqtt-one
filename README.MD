# MQTT One Node

One MQTT node for all connections. Fully dynamic and controlled by the incoming message.

### Incoming Message Example
```typescript
interface ISubscribeMessage {
  command: "__subscribe", // to unsubscribe send payload.subscriptions = []
  brokerId?: string | number,
  payload?: {
      subscriptions?: string[],
  }
}

interface IPublishMessage {
  command: "__publish",
  brokerId?: string | number,
  topic?: string;
  payload?: any,
  opts?: {
    qos?: number,
    retain?: boolean
  }
}

interface IAddBrokerMessage {
  command: "__add_broker",
  brokerId?: string | number,
  payload?: {
      subscriptions?: string[],
      options?: {
          protocol: 'wss' | 'ws' | 'mqtt' | 'mqtts' | 'tcp' | 'ssl' | 'wx' | 'wxs'
          port: number
          host: string
          hostname: string
          username: string,
          password: string,
          path?: string
          keepalive?: number
          clientId?: string
          protocolId?: string
          protocolVersion?: number
          clean?: boolean,
          brokerId?: string | number
      }
  }
}
```

### Outgoing Message Example
```typescript
interface IMqttMessage {
  brokerId: string | number,
  topic: string, // mqtt topic or '__status/connection' or '__status/error'
  payload: any
}
```
