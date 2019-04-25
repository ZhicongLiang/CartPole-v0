# CartPole-v0
Reproducing https://pytorch.org/tutorials/intermediate/reinforcement_q_learning.html

## key steps:

initializer policy_net  
initializer target_net = policy_net  

<br/>

In each episode:  
  * initializer env  
  *  In each step:  
  *  get s_t  
  *  action_value = policy_net(s_t)  
  *  a_t = mixture(random aciton, max_{a_t}(aciton_value))  
  *  get s_t+1, reward by env.step(a_t)  
  *  store(s_t, a_t, reward, s_t+1)  
  *  optimizer:  
    * sample (s_t, a_t, reward, s_t+1) batch  
    * state_aciton_value = policy(state_batch)  
    * next_state_value = target_net(next_state)  
    * expected_state_action_values = (next_state_value * GAMMA + reward_batch  
    * # bellman equation:  
    * loss = HuberLoss(state_action_values, expected_state_aciton_values)  
    * loss.bachward()  
