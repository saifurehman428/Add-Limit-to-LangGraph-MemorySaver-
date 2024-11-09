# Message-Limited In-Memory Chat Memory Solution

When building conversational agents, memory management is crucial, especially in long-running sessions where the memory may grow indefinitely. This solution provides a way to limit the memory usage by removing older messages directly from the in-memory state.

## Problem
In some implementations, such as the `MemorySaver` setup, messages are stored in memory and passed to the LLM (Language Model) based on a recent `k`-message limit. However, even if only the last `k` messages are passed to the LLM, the memory continues to store all messages in the state, potentially leading to an overflow as more messages accumulate over time.

## Solution: Limited State Retention

We introduce an additional node in the conversation graph that actively removes older messages from memory. By setting a limit, this node will ensure that the in-memory state always retains only the most recent `n` messages, effectively keeping memory usage in check.
