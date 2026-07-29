## amazon api gateway
1. managed service to easily publish, create, maintain, monitor and secure your api.
2. front door to your app.
3. integrates with lambda and others.
4. compatible with swagger and openapi.
5. allows to easily transform and validate incoming api reqs.
6. api gw endpoint types
   1. edge-optimized - default option. API reqs get sent thru cf edge location. Best for global user. GW is still deployed to a single region.
   2. regional - perfect for clients that reside in same region.
   3. private - only accessible via VPC using vpc interface endpts.
7. API types
   1. rest api - collection of http resources and methods integrated with lambda, http endpts, and other aws svcs.
   2. http api - simpler rest api. Cheaper and minimal features.
   3. WebSocket api - invoked via frontend websocket.
8. use case
   1. deploy restful api in front of amazon kinesis data streams for real-time ingestion.