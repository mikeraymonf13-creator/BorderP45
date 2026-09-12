# BorderP45
BorderP45 TypeScript backend with CaptchaLa validation and TON Connect integration// routes/ton-connect.ts
import express from 'express';
import { validateCaptchaToken } from '../captcha-validation';

const router = express.Router();

router.post('/ton-connect', async (req, res) => {
  const { pass_token } = req.body;

  // Validate CAPTCHA
  const captchaResult = await validateCaptchaToken(pass_token);
  if (!captchaResult.success) {
    return res.status(403).json({ error: 'CAPTCHA validation failed' });
  }

  // Proceed to TON Connect logic
  // ...
  res.json({ message: 'Proceeding to TON Connect' });
});

export default router;
